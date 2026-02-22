 Overview
This project demonstrates the implementation of **Level Order Traversal** (also known as **Breadth-First Search - BFS**) in a Binary Tree using C.

The program:

- ✅ Creates a binary tree manually  
- ✅ Implements a simple queue using an array  
- ✅ Performs Level Order Traversal  

Level Order Traversal visits nodes **level by level from left to right**.

--

 Source Code

```c
#include <stdio.h>
#include <stdlib.h>

// Structure of Node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Create new node
struct Node* createNode(int value) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

// Simple queue implementation for tree nodes
struct Node* queue[100];
int front = -1, rear = -1;

void enqueue(struct Node* node) {
    if (rear == 99)
        return;
    if (front == -1)
        front = 0;
    queue[++rear] = node;
}

struct Node* dequeue() {
    if (front == -1 || front > rear)
        return NULL;
    return queue[front++];
}

// Level Order Traversal
void levelOrder(struct Node* root) {
    if (root == NULL)
        return;

    enqueue(root);

    while (front <= rear) {
        struct Node* temp = dequeue();
        printf("%d ", temp->data);

        if (temp->left != NULL)
            enqueue(temp->left);

        if (temp->right != NULL)
            enqueue(temp->right);
    }
}

// Main function
int main() {
    struct Node* root = NULL;

    // Creating sample tree manually
    root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Level Order Traversal: ");
    levelOrder(root);

    return 0;
}
```

---

 What is Level Order Traversal?

Level Order Traversal is a tree traversal technique where:

- Nodes are visited **level by level**
- From **left to right**
- Uses a **Queue (FIFO - First In First Out)**

It is also known as:

> 🔹 Breadth-First Search (BFS)

---

 How It Works

1. Insert root node into queue.
2. Repeat until queue is empty:
   - Remove node from front.
   - Print its data.
   - Insert left child (if exists).
   - Insert right child (if exists).

---

 Tree Used in This Example

```
        1
       / \
      2   3
     / \
    4   5
```

---

 Sample Output

```
Level Order Traversal: 1 2 3 4 5
```

---

 Time and Space Complexity

- **Time Complexity:** O(n)  
- **Space Complexity:** O(n)  

Where `n` is the number of nodes in the tree.

---

 How to Compile and Run

 Compile:
```
gcc level_order.c -o level
```

 Run:
```
./level
```

---

 Concepts Used

- Binary Tree
- Breadth-First Search (BFS)
- Queue using Array
- Dynamic Memory Allocation (`malloc`)
- Pointers and Structures in C
