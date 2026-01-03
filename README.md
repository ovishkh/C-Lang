# C Programming: Basic to Advanced Tutorial

## 1. Environment Setup

### Install Compiler
- **Windows**: MinGW or TDM-GCC
- **Linux**: `sudo apt-get install gcc`
- **macOS**: `xcode-select --install`

### Verify Installation
```bash
gcc --version
```

---

## 2. First Program

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

**Compilation & Execution:**
```bash
gcc hello.c -o hello
./hello
```

**Explanation:**
- `#include <stdio.h>`: Preprocessor directive importing standard input/output library
- `int main()`: Entry point, returns integer to OS
- `printf()`: Outputs formatted text to stdout
- `return 0`: Indicates successful execution

---

## 3. Data Types & Variables

### Basic Types

```c
#include <stdio.h>

int main() {
    int age = 25;              // 4 bytes, range: -2,147,483,648 to 2,147,483,647
    float height = 5.9;        // 4 bytes, ~7 decimal digits precision
    double weight = 70.5;      // 8 bytes, ~15 decimal digits precision
    char grade = 'A';          // 1 byte, single character
    
    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Weight: %.2lf\n", weight);
    printf("Grade: %c\n", grade);
    
    return 0;
}
```

**Format Specifiers:**
- `%d`: int
- `%f`: float
- `%lf`: double
- `%c`: char
- `%s`: string
- `%p`: pointer address

### Type Modifiers

```c
short int si = 32767;          // 2 bytes
long int li = 2147483647L;     // 4/8 bytes
unsigned int ui = 4294967295U; // No negative values
long long ll = 9223372036854775807LL; // 8 bytes
```

---

## 4. Operators

```c
#include <stdio.h>

int main() {
    int a = 10, b = 3;
    
    // Arithmetic
    printf("a + b = %d\n", a + b);  // 13
    printf("a - b = %d\n", a - b);  // 7
    printf("a * b = %d\n", a * b);  // 30
    printf("a / b = %d\n", a / b);  // 3 (integer division)
    printf("a %% b = %d\n", a % b); // 1 (modulo)
    
    // Relational
    printf("a > b: %d\n", a > b);   // 1 (true)
    printf("a == b: %d\n", a == b); // 0 (false)
    
    // Logical
    int x = 1, y = 0;
    printf("x && y: %d\n", x && y); // 0 (AND)
    printf("x || y: %d\n", x || y); // 1 (OR)
    printf("!x: %d\n", !x);         // 0 (NOT)
    
    // Bitwise
    printf("a & b: %d\n", a & b);   // 2 (bitwise AND)
    printf("a | b: %d\n", a | b);   // 11 (bitwise OR)
    printf("a ^ b: %d\n", a ^ b);   // 9 (XOR)
    printf("a << 1: %d\n", a << 1); // 20 (left shift)
    printf("a >> 1: %d\n", a >> 1); // 5 (right shift)
    
    // Increment/Decrement
    int c = 5;
    printf("c++: %d\n", c++); // 5 (post-increment, returns then increments)
    printf("c: %d\n", c);     // 6
    printf("++c: %d\n", ++c); // 7 (pre-increment, increments then returns)
    
    return 0;
}
```

---

## 5. Control Structures

### If-Else

```c
#include <stdio.h>

int main() {
    int num = 15;
    
    if (num > 0) {
        printf("Positive\n");
    } else if (num < 0) {
        printf("Negative\n");
    } else {
        printf("Zero\n");
    }
    
    // Ternary operator
    char *result = (num % 2 == 0) ? "Even" : "Odd";
    printf("%s\n", result);
    
    return 0;
}
```

### Switch

```c
#include <stdio.h>

int main() {
    int day = 3;
    
    switch(day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        default:
            printf("Invalid day\n");
    }
    
    return 0;
}
```

### Loops

```c
#include <stdio.h>

int main() {
    // For loop
    for (int i = 0; i < 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    
    // While loop
    int j = 0;
    while (j < 5) {
        printf("%d ", j);
        j++;
    }
    printf("\n");
    
    // Do-while loop
    int k = 0;
    do {
        printf("%d ", k);
        k++;
    } while (k < 5);
    printf("\n");
    
    // Break and continue
    for (int i = 0; i < 10; i++) {
        if (i == 3) continue; // Skip 3
        if (i == 7) break;    // Stop at 7
        printf("%d ", i);
    }
    printf("\n");
    
    return 0;
}
```

---

## 6. Functions

```c
#include <stdio.h>

// Function declaration (prototype)
int add(int a, int b);
void greet(char name[]);
int factorial(int n);

int main() {
    int sum = add(5, 3);
    printf("Sum: %d\n", sum);
    
    greet("Alice");
    
    printf("Factorial of 5: %d\n", factorial(5));
    
    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;
}

void greet(char name[]) {
    printf("Hello, %s!\n", name);
}

// Recursive function
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

**Pass by Value vs Reference:**

```c
#include <stdio.h>

void passByValue(int x) {
    x = 100; // Original unchanged
}

void passByReference(int *x) {
    *x = 100; // Original modified
}

int main() {
    int num = 10;
    
    passByValue(num);
    printf("After pass by value: %d\n", num); // 10
    
    passByReference(&num);
    printf("After pass by reference: %d\n", num); // 100
    
    return 0;
}
```

---

## 7. Arrays

### One-Dimensional Arrays

```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    
    // Access elements
    printf("First element: %d\n", arr[0]);
    printf("Last element: %d\n", arr[4]);
    
    // Iterate
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    // Partial initialization
    int partial[5] = {1, 2}; // Remaining elements = 0
    
    // Size calculation
    int size = sizeof(arr) / sizeof(arr[0]);
    printf("Array size: %d\n", size);
    
    return 0;
}
```

### Multi-Dimensional Arrays

```c
#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    
    // Access elements
    printf("Element at [1][2]: %d\n", matrix[1][2]); // 6
    
    // Iterate
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### Array Functions

```c
#include <stdio.h>

int findMax(int arr[], int size) {
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max) max = arr[i];
    }
    return max;
}

void reverseArray(int arr[], int size) {
    for (int i = 0; i < size / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[size - 1 - i];
        arr[size - 1 - i] = temp;
    }
}

int main() {
    int numbers[] = {5, 2, 8, 1, 9};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    printf("Max: %d\n", findMax(numbers, size));
    
    reverseArray(numbers, size);
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");
    
    return 0;
}
```

---

## 8. Pointers

### Basic Pointers

```c
#include <stdio.h>

int main() {
    int var = 10;
    int *ptr = &var; // Pointer stores address of var
    
    printf("Value of var: %d\n", var);
    printf("Address of var: %p\n", (void*)&var);
    printf("Value of ptr: %p\n", (void*)ptr);
    printf("Value pointed by ptr: %d\n", *ptr); // Dereferencing
    
    *ptr = 20; // Modify value through pointer
    printf("New value of var: %d\n", var);
    
    return 0;
}
```

### Pointer Arithmetic

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int *ptr = arr; // Array name is pointer to first element
    
    printf("First element: %d\n", *ptr);
    printf("Second element: %d\n", *(ptr + 1));
    
    // Iterate using pointer
    for (int i = 0; i < 5; i++) {
        printf("%d ", *(ptr + i));
    }
    printf("\n");
    
    // Pointer increment
    ptr++;
    printf("After increment: %d\n", *ptr); // 20
    
    return 0;
}
```

### Pointers to Pointers

```c
#include <stdio.h>

int main() {
    int var = 10;
    int *ptr1 = &var;
    int **ptr2 = &ptr1; // Pointer to pointer
    
    printf("Value: %d\n", var);
    printf("Via ptr1: %d\n", *ptr1);
    printf("Via ptr2: %d\n", **ptr2);
    
    **ptr2 = 30;
    printf("Modified value: %d\n", var);
    
    return 0;
}
```

### Function Pointers

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int multiply(int a, int b) {
    return a * b;
}

int main() {
    int (*operation)(int, int); // Function pointer declaration
    
    operation = add;
    printf("Add: %d\n", operation(5, 3));
    
    operation = multiply;
    printf("Multiply: %d\n", operation(5, 3));
    
    return 0;
}
```

---

## 9. Strings

```c
#include <stdio.h>
#include <string.h>

int main() {
    // Declaration methods
    char str1[] = "Hello";
    char str2[20] = "World";
    char *str3 = "Pointer";
    
    printf("%s\n", str1);
    
    // String functions
    printf("Length: %lu\n", strlen(str1));
    
    char dest[20];
    strcpy(dest, str1); // Copy
    printf("Copied: %s\n", dest);
    
    strcat(dest, " "); // Concatenate
    strcat(dest, str2);
    printf("Concatenated: %s\n", dest);
    
    int cmp = strcmp(str1, str2); // Compare
    printf("Comparison: %d\n", cmp);
    
    // Character access
    for (int i = 0; str1[i] != '\0'; i++) {
        printf("%c ", str1[i]);
    }
    printf("\n");
    
    // Input
    char input[50];
    printf("Enter string: ");
    fgets(input, sizeof(input), stdin);
    input[strcspn(input, "\n")] = 0; // Remove newline
    printf("You entered: %s\n", input);
    
    return 0;
}
```

---

## 10. Structures

```c
#include <stdio.h>
#include <string.h>

// Structure definition
struct Student {
    int id;
    char name[50];
    float gpa;
};

// Typedef for cleaner syntax
typedef struct {
    int x;
    int y;
} Point;

int main() {
    // Initialization
    struct Student s1 = {1, "Alice", 3.8};
    struct Student s2;
    
    s2.id = 2;
    strcpy(s2.name, "Bob");
    s2.gpa = 3.5;
    
    printf("Student 1: %d, %s, %.2f\n", s1.id, s1.name, s1.gpa);
    
    // Array of structures
    struct Student students[3] = {
        {1, "Alice", 3.8},
        {2, "Bob", 3.5},
        {3, "Charlie", 3.9}
    };
    
    for (int i = 0; i < 3; i++) {
        printf("%d: %s (%.2f)\n", students[i].id, students[i].name, students[i].gpa);
    }
    
    // Using typedef
    Point p1 = {10, 20};
    printf("Point: (%d, %d)\n", p1.x, p1.y);
    
    // Pointer to structure
    struct Student *ptr = &s1;
    printf("Via pointer: %s\n", ptr->name);
    
    return 0;
}
```

### Nested Structures

```c
#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};

struct Employee {
    int id;
    char name[50];
    struct Date joinDate;
};

int main() {
    struct Employee emp = {101, "John", {15, 8, 2020}};
    
    printf("Employee: %s\n", emp.name);
    printf("Join Date: %d/%d/%d\n", emp.joinDate.day, emp.joinDate.month, emp.joinDate.year);
    
    return 0;
}
```

---

## 11. Unions

```c
#include <stdio.h>

union Data {
    int i;
    float f;
    char str[20];
};

int main() {
    union Data data;
    
    data.i = 10;
    printf("data.i: %d\n", data.i);
    
    data.f = 220.5; // Overwrites previous value
    printf("data.f: %.2f\n", data.f);
    
    printf("Union size: %lu bytes\n", sizeof(data));
    
    return 0;
}
```

**Difference from Struct:**
- Union: All members share same memory location; size = largest member
- Struct: Each member has separate memory; size = sum of all members

---

## 12. Enums

```c
#include <stdio.h>

enum Weekday {
    MONDAY,    // 0
    TUESDAY,   // 1
    WEDNESDAY, // 2
    THURSDAY,  // 3
    FRIDAY,    // 4
    SATURDAY,  // 5
    SUNDAY     // 6
};

enum Status {
    SUCCESS = 1,
    FAILURE = -1,
    PENDING = 0
};

int main() {
    enum Weekday today = WEDNESDAY;
    
    if (today == WEDNESDAY) {
        printf("It's Wednesday!\n");
    }
    
    printf("Value: %d\n", today);
    
    enum Status result = SUCCESS;
    printf("Status: %d\n", result);
    
    return 0;
}
```

---

## 13. File I/O

### Basic File Operations

```c
#include <stdio.h>

int main() {
    FILE *fp;
    char content[100];
    
    // Write to file
    fp = fopen("test.txt", "w");
    if (fp == NULL) {
        printf("Error opening file\n");
        return 1;
    }
    fprintf(fp, "Hello, File!\n");
    fprintf(fp, "Line 2\n");
    fclose(fp);
    
    // Read from file
    fp = fopen("test.txt", "r");
    if (fp == NULL) {
        printf("Error opening file\n");
        return 1;
    }
    while (fgets(content, sizeof(content), fp) != NULL) {
        printf("%s", content);
    }
    fclose(fp);
    
    return 0;
}
```

### File Modes

- `"r"`: Read (file must exist)
- `"w"`: Write (creates new/overwrites)
- `"a"`: Append (creates if doesn't exist)
- `"r+"`: Read/Write (file must exist)
- `"w+"`: Read/Write (creates new/overwrites)
- `"a+"`: Read/Append

### Binary Files

```c
#include <stdio.h>

struct Record {
    int id;
    char name[50];
};

int main() {
    FILE *fp;
    struct Record r1 = {1, "Alice"};
    struct Record r2;
    
    // Write binary
    fp = fopen("data.bin", "wb");
    fwrite(&r1, sizeof(struct Record), 1, fp);
    fclose(fp);
    
    // Read binary
    fp = fopen("data.bin", "rb");
    fread(&r2, sizeof(struct Record), 1, fp);
    printf("ID: %d, Name: %s\n", r2.id, r2.name);
    fclose(fp);
    
    return 0;
}
```

---

## 14. Dynamic Memory Allocation

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    int n = 5;
    
    // malloc - allocates uninitialized memory
    ptr = (int*) malloc(n * sizeof(int));
    if (ptr == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }
    
    for (int i = 0; i < n; i++) {
        ptr[i] = i + 1;
    }
    
    for (int i = 0; i < n; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    free(ptr); // Deallocate memory
    
    // calloc - allocates zero-initialized memory
    ptr = (int*) calloc(n, sizeof(int));
    
    for (int i = 0; i < n; i++) {
        printf("%d ", ptr[i]); // All zeros
    }
    printf("\n");
    
    // realloc - resize allocated memory
    ptr = (int*) realloc(ptr, 10 * sizeof(int));
    
    for (int i = n; i < 10; i++) {
        ptr[i] = i + 1;
    }
    
    for (int i = 0; i < 10; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    free(ptr);
    
    return 0;
}
```

---

## 15. Preprocessor Directives

```c
#include <stdio.h>

// Macros
#define PI 3.14159
#define SQUARE(x) ((x) * (x))
#define MAX(a, b) ((a) > (b) ? (a) : (b))

// Conditional compilation
#define DEBUG 1

int main() {
    printf("PI: %.5f\n", PI);
    printf("Square of 5: %d\n", SQUARE(5));
    printf("Max of 10 and 20: %d\n", MAX(10, 20));
    
    #ifdef DEBUG
        printf("Debug mode enabled\n");
    #endif
    
    #if DEBUG == 1
        printf("Debug level 1\n");
    #elif DEBUG == 2
        printf("Debug level 2\n");
    #else
        printf("Debug disabled\n");
    #endif
    
    printf("File: %s\n", __FILE__);
    printf("Line: %d\n", __LINE__);
    printf("Date: %s\n", __DATE__);
    printf("Time: %s\n", __TIME__);
    
    return 0;
}
```

---

## 16. Command Line Arguments

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    printf("Number of arguments: %d\n", argc);
    
    for (int i = 0; i < argc; i++) {
        printf("Argument %d: %s\n", i, argv[i]);
    }
    
    if (argc > 1) {
        int num = atoi(argv[1]); // Convert string to int
        printf("First argument as integer: %d\n", num);
    }
    
    return 0;
}
```

**Compilation & Execution:**
```bash
gcc program.c -o program
./program arg1 arg2 arg3
```

---

## 17. Advanced Data Structures

### Linked List

```c
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node *next;
};

void insertAtBeginning(struct Node **head, int data) {
    struct Node *newNode = (struct Node*) malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = *head;
    *head = newNode;
}

void display(struct Node *head) {
    struct Node *temp = head;
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");
}

void deleteNode(struct Node **head, int key) {
    struct Node *temp = *head;
    struct Node *prev = NULL;
    
    if (temp != NULL && temp->data == key) {
        *head = temp->next;
        free(temp);
        return;
    }
    
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }
    
    if (temp == NULL) return;
    
    prev->next = temp->next;
    free(temp);
}

int main() {
    struct Node *head = NULL;
    
    insertAtBeginning(&head, 3);
    insertAtBeginning(&head, 2);
    insertAtBeginning(&head, 1);
    
    display(head);
    
    deleteNode(&head, 2);
    display(head);
    
    return 0;
}
```

### Stack

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 100

struct Stack {
    int items[MAX];
    int top;
};

void initialize(struct Stack *s) {
    s->top = -1;
}

int isEmpty(struct Stack *s) {
    return s->top == -1;
}

int isFull(struct Stack *s) {
    return s->top == MAX - 1;
}

void push(struct Stack *s, int value) {
    if (isFull(s)) {
        printf("Stack overflow\n");
        return;
    }
    s->items[++(s->top)] = value;
}

int pop(struct Stack *s) {
    if (isEmpty(s)) {
        printf("Stack underflow\n");
        return -1;
    }
    return s->items[(s->top)--];
}

int peek(struct Stack *s) {
    if (isEmpty(s)) {
        return -1;
    }
    return s->items[s->top];
}

int main() {
    struct Stack s;
    initialize(&s);
    
    push(&s, 10);
    push(&s, 20);
    push(&s, 30);
    
    printf("Top element: %d\n", peek(&s));
    printf("Popped: %d\n", pop(&s));
    printf("Popped: %d\n", pop(&s));
    
    return 0;
}
```

### Queue

```c
#include <stdio.h>
#include <stdlib.h>

#define MAX 100

struct Queue {
    int items[MAX];
    int front;
    int rear;
};

void initialize(struct Queue *q) {
    q->front = -1;
    q->rear = -1;
}

int isEmpty(struct Queue *q) {
    return q->front == -1;
}

int isFull(struct Queue *q) {
    return q->rear == MAX - 1;
}

void enqueue(struct Queue *q, int value) {
    if (isFull(q)) {
        printf("Queue full\n");
        return;
    }
    if (q->front == -1) q->front = 0;
    q->items[++(q->rear)] = value;
}

int dequeue(struct Queue *q) {
    if (isEmpty(q)) {
        printf("Queue empty\n");
        return -1;
    }
    int value = q->items[q->front];
    if (q->front >= q->rear) {
        q->front = q->rear = -1;
    } else {
        q->front++;
    }
    return value;
}

int main() {
    struct Queue q;
    initialize(&q);
    
    enqueue(&q, 10);
    enqueue(&q, 20);
    enqueue(&q, 30);
    
    printf("Dequeued: %d\n", dequeue(&q));
    printf("Dequeued: %d\n", dequeue(&q));
    
    return 0;
}
```

---

## 18. Sorting Algorithms

### Bubble Sort

```c
#include <stdio.h>

void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    bubbleSort(arr, n);
    
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Quick Sort

```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[i + 1], &arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    quickSort(arr, 0, n - 1);
    
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

---

## 19. Searching Algorithms

### Linear Search

```c
#include <stdio.h>

int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 10;
    
    int result = linearSearch(arr, n, key);
    if (result != -1) {
        printf("Element found at index %d\n", result);
    } else {
        printf("Element not found\n");
    }
    
    return 0;
}
```

### Binary Search

```c
#include <stdio.h>

int binarySearch(int arr[], int low, int high, int key) {
    while (low <= high) {
        int mid = low + (high - low) / 2;
        
        if (arr[mid] == key) return mid;
        if (arr[mid] < key) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 10;
    
    int result = binarySearch(arr, 0, n -1, key);

    if (result != -1) {
        printf("Element found at index %d\n", result);
    } else {
        printf("Element not found\n");
    }
    
    return 0;
}
```

---

## 20. Bitwise Manipulation

```c
#include <stdio.h>

void printBinary(int n) {
    for (int i = 31; i >= 0; i--) {
        int bit = (n >> i) & 1;
        printf("%d", bit);
        if (i % 8 == 0) printf(" ");
    }
    printf("\n");
}

int main() {
    int a = 5;  // 0101
    int b = 3;  // 0011
    
    printf("a = %d: ", a);
    printBinary(a);
    
    printf("b = %d: ", b);
    printBinary(b);
    
    printf("a & b = %d\n", a & b);   // 0001 = 1
    printf("a | b = %d\n", a | b);   // 0111 = 7
    printf("a ^ b = %d\n", a ^ b);   // 0110 = 6
    printf("~a = %d\n", ~a);         // Flip all bits
    printf("a << 1 = %d\n", a << 1); // 1010 = 10
    printf("a >> 1 = %d\n", a >> 1); // 0010 = 2
    
    // Check if number is power of 2
    int n = 16;
    if (n > 0 && (n & (n - 1)) == 0) {
        printf("%d is power of 2\n", n);
    }
    
    // Count set bits
    int count = 0;
    int num = 15; // 1111
    while (num) {
        count += num & 1;
        num >>= 1;
    }
    printf("Set bits in 15: %d\n", count);
    
    return 0;
}
```

---

## 21. Error Handling

```c
#include <stdio.h>
#include <errno.h>
#include <string.h>

int divide(int a, int b, int *result) {
    if (b == 0) {
        return -1; // Error code
    }
    *result = a / b;
    return 0; // Success
}

int main() {
    FILE *fp;
    
    // File error handling
    fp = fopen("nonexistent.txt", "r");
    if (fp == NULL) {
        printf("Error: %s\n", strerror(errno));
        perror("File opening failed");
    }
    
    // Function error handling
    int result;
    if (divide(10, 0, &result) != 0) {
        printf("Division error: Cannot divide by zero\n");
    } else {
        printf("Result: %d\n", result);
    }
    
    if (divide(10, 2, &result) == 0) {
        printf("Result: %d\n", result);
    }
    
    return 0;
}
```

---

## 22. Multi-file Programs

**main.c:**
```c
#include <stdio.h>
#include "calculator.h"

int main() {
    printf("Sum: %d\n", add(5, 3));
    printf("Product: %d\n", multiply(5, 3));
    return 0;
}
```

**calculator.h:**
```c
#ifndef CALCULATOR_H
#define CALCULATOR_H

int add(int a, int b);
int multiply(int a, int b);

#endif
```

**calculator.c:**
```c
#include "calculator.h"

int add(int a, int b) {
    return a + b;
}

int multiply(int a, int b) {
    return a * b;
}
```

**Compilation:**
```bash
gcc main.c calculator.c -o program
./program
```

---

## 23. Advanced Pointer Techniques

### Array of Pointers

```c
#include <stdio.h>

int main() {
    char *names[] = {"Alice", "Bob", "Charlie"};
    
    for (int i = 0; i < 3; i++) {
        printf("%s\n", names[i]);
    }
    
    return 0;
}
```

### Pointer to Array

```c
#include <stdio.h>

int main() {
    int arr[3] = {10, 20, 30};
    int (*ptr)[3] = &arr; // Pointer to array of 3 integers
    
    for (int i = 0; i < 3; i++) {
        printf("%d ", (*ptr)[i]);
    }
    printf("\n");
    
    return 0;
}
```

### Void Pointers

```c
#include <stdio.h>

int main() {
    int i = 10;
    float f = 3.14;
    char c = 'A';
    
    void *ptr;
    
    ptr = &i;
    printf("Integer: %d\n", *(int*)ptr);
    
    ptr = &f;
    printf("Float: %.2f\n", *(float*)ptr);
    
    ptr = &c;
    printf("Char: %c\n", *(char*)ptr);
    
    return 0;
}
```

---

## 24. Memory Management Best Practices

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* createString(const char *str) {
    char *newStr = (char*) malloc(strlen(str) + 1);
    if (newStr == NULL) {
        return NULL;
    }
    strcpy(newStr, str);
    return newStr;
}

int main() {
    char *str = createString("Hello");
    if (str == NULL) {
        printf("Memory allocation failed\n");
        return 1;
    }
    
    printf("%s\n", str);
    
    free(str); // Always free allocated memory
    str = NULL; // Prevent dangling pointer
    
    // Memory leak example (avoid this)
    // int *leak = malloc(sizeof(int));
    // No free() - memory leaked
    
    return 0;
}
```

---

## 25. Complete Project Example: Student Management System

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_STUDENTS 100

typedef struct {
    int id;
    char name[50];
    float gpa;
} Student;

Student students[MAX_STUDENTS];
int studentCount = 0;

void addStudent() {
    if (studentCount >= MAX_STUDENTS) {
        printf("Database full\n");
        return;
    }
    
    Student s;
    printf("Enter ID: ");
    scanf("%d", &s.id);
    printf("Enter Name: ");
    scanf(" %[^\n]", s.name);
    printf("Enter GPA: ");
    scanf("%f", &s.gpa);
    
    students[studentCount++] = s;
    printf("Student added successfully\n");
}

void displayStudents() {
    if (studentCount == 0) {
        printf("No students in database\n");
        return;
    }
    
    printf("\n%-5s %-30s %-5s\n", "ID", "Name", "GPA");
    printf("----------------------------------------\n");
    for (int i = 0; i < studentCount; i++) {
        printf("%-5d %-30s %.2f\n", students[i].id, students[i].name, students[i].gpa);
    }
}

void searchStudent() {
    int id;
    printf("Enter student ID: ");
    scanf("%d", &id);
    
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            printf("Found: %d - %s - %.2f\n", students[i].id, students[i].name, students[i].gpa);
            return;
        }
    }
    printf("Student not found\n");
}

void deleteStudent() {
    int id;
    printf("Enter student ID to delete: ");
    scanf("%d", &id);
    
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            for (int j = i; j < studentCount - 1; j++) {
                students[j] = students[j + 1];
            }
            studentCount--;
            printf("Student deleted successfully\n");
            return;
        }
    }
    printf("Student not found\n");
}

void saveToFile() {
    FILE *fp = fopen("students.dat", "wb");
    if (fp == NULL) {
        printf("Error opening file\n");
        return;
    }
    
    fwrite(&studentCount, sizeof(int), 1, fp);
    fwrite(students, sizeof(Student), studentCount, fp);
    fclose(fp);
    printf("Data saved successfully\n");
}

void loadFromFile() {
    FILE *fp = fopen("students.dat", "rb");
    if (fp == NULL) {
        printf("No existing data file\n");
        return;
    }
    
    fread(&studentCount, sizeof(int), 1, fp);
    fread(students, sizeof(Student), studentCount, fp);
    fclose(fp);
    printf("Data loaded successfully\n");
}

int main() {
    int choice;
    
    loadFromFile();
    
    while (1) {
        printf("\n=== Student Management System ===\n");
        printf("1. Add Student\n");
        printf("2. Display Students\n");
        printf("3. Search Student\n");
        printf("4. Delete Student\n");
        printf("5. Save to File\n");
        printf("6. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1:
                addStudent();
                break;
            case 2:
                displayStudents();
                break;
            case 3:
                searchStudent();
                break;
            case 4:
                deleteStudent();
                break;
            case 5:
                saveToFile();
                break;
            case 6:
                saveToFile();
                printf("Exiting...\n");
                return 0;
            default:
                printf("Invalid choice\n");
        }
    }
    
    return 0;
}
```

---

## Compilation Tips

**Basic compilation:**
```bash
gcc program.c -o program
```

**With warnings:**
```bash
gcc -Wall -Wextra program.c -o program
```

**Optimization:**
```bash
gcc -O2 program.c -o program
```

**Debug mode:**
```bash
gcc -g program.c -o program
gdb program
```

**Multiple files:**
```bash
gcc file1.c file2.c file3.c -o program
```

**With math library:**
```bash
gcc program.c -o program -lm
```
