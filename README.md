Download Link: https://assignmentchef.com/product/solved-comp-348-principles-of-programming-languages-assignment-2-on-lisp-and-c-2
<br>



<h1><a name="_Toc9919"></a>1          General Information</h1>




<h1><a name="_Toc9920"></a>2          Introduction</h1>

This assignment targets two programming paradigms: 1) Functional Programming with Lisp, 2) Procedural Programming with C.

<h1><a name="_Toc9921"></a>3          Ground rules</h1>

You are allowed to work on a team of 3 students at most (including yourself). Each team should designate a leader who will submit the assignment electronically. See Submission Notes for the details.

ONLY one copy of the assignment is to be submitted by the team leader. Upon submission, you must book an appointment with the marker team and demo the assignment. All members of the team must be present during the demo to receive the credit. Failure to do so may result in zero credit.

This is an assessment exercise. You may not seek any assistance from others while expecting to receive credit. You must work strictly within your team). Failure to do so will result in penalties or no credit.

<h1><a name="_Toc9922"></a>4          Your Assignment</h1>

Your assignment is given in two parts, as follows. 1) Functional Programming with Lisp, 2) Procedural Programming with C.

<h2><a name="_Toc9923"></a>4.1         Functional Programming with Lisp</h2>

List Processing

For the following questions, implement the function in lisp. Some examples are provided to illustrate the behaviour of each function. Your implementation, however must consider all possible inputs.

Q 1. Write a lisp function called sub-list that takes a list and two indexes from and to, and returns a list whose elements are the elements of the input list within from and to indexes.

The argument to is optional, and in case it is omitted (default to NIL), the list length is logically considered as its value. In case the indexes do not have proper values (i.e. are

out of bound), the function simply returns NIL (see examples).

Examples:

&gt; (sub-list ’(1 6 12) 2 3)

(6 12)

&gt; (sub-list ’(1 6 12) 1 4)

NIL

&gt; (sub-list ’(1 6 12) 0 1)

NIL

&gt; (sub-list ’(1 6 12) 4 2)

NIL

&gt; (sub-list ’(1 6 12))

ERROR *** – EVAL/APPLY: Too few arguments

NOTE: You may NOT use any built-in functions other than car, cdr, the list construction functions: cons, list, append, or list-length.

Hint: Use NIL as the default value for the optional to parameter.

Q 2. Write a lisp function that receives a list as the input argument (the list is mixed up integers, decimals, characters and nested lists) and returns a attened list containing all the atomic elements without any duplication. Sample function output is shown below:

(flatten-nodup ’(1 2 (3 1) (a 2.5) (2 4.5) ((1 2))))

(1 2 3 a 2.5 4.5)

Q 3. Write a list function that receives a single argument and determines its depth. The depth of an atom is considered 0; the depth of a list with no inner list is considered 1; the depth of a list with inner lists, would the maximum dept of its elements plus 1.

Examples:

&gt; (depth NIL)

0

&gt; (depth 1)

0

&gt; (depth ’(1))

1

&gt; (depth ’((2)))

2

&gt; (depth ’((2)(3 (6))(4)))

3

Q 4. In previous assignment, you wrote a Prolog query to generate the rst n numbers of the Lucas sequence. In this assignment, rewrite the code in lisp so that your function generates the sequence and <u>returns </u>the result as a list.

Structures

Q 5. Write a lisp function cog that receives a list and calculates its center of gravity. The center of gravity is de ned as follows.

Suppose a list represents a bar with weights attached to the positions at indexes. Suppose the mid-point is represented by 0. The center of gravity is the distance from the midpoint where a positive value represents leaning towards right.

The center of gravity may be calculated by applying a simple weighted averaging over indexes, as demonstrated in the following example:

’(a (b c) d (e (f g)))

pos:       1    2                3                4 — + — – — + — * — + — – — + -a            |                d                | +–+–+ +–+–+ | |                |      |

b              c                                   e        +–+–


|              |

* = midpoint                                                                          f              g

The center of gravity may be obtain using the following formula:

cog <em>,</em>

where <em>N </em>is the length of the list, and <em>n<sub>i </sub></em>is the total number of weights (elements) attached at position <em>i</em>.

cog = (1×(1−2<em>.</em>5)+2×(2−2<em>.</em>5)+1×(3−2<em>.</em>5)+3×(4−2<em>.</em>5))<em>/</em>(7) = 0<em>.</em>357.

Examples:

&gt; (cog ’(a (b c) d (e (f g))))

0.3571428571428571

&gt; (cog ’(a (b c) d (e f)))

0.1666666666666667

&gt; (cog ’(a (b c) (e f) d))

0

&gt; (cog ’(1 2 3 4 5))

0

&gt; (cog ’(1 2 3 4 5 6))

0

Q 6. Write a lisp function to check whether a binary tree is a Binary Search Tree. A Binary Search Tree (BST) is a tree in which all the nodes follow the below-mentioned properties:

The left sub-tree of a node has a key less than or equal to its parent node’s key.

The right sub-tree of a node has a key greater than to its parent node’s key.

A list representing the structure of a sample binary tree is given in the following:

’(8 (3 (1 () ()) (6 (4 () ())(7 () ()))) (10 () (14 (13 () ()) ())))

Q 7. Write a lisp function inorder that receives a tree (using the same structure as in the previous question), and returns its in-order traversal of the tree in the form of a list. An example of the in-order traversal of the tree in the previous question is given in the following:

(inorder ’(8 (3 (1 () ()) (6 (4 () ())(7 () ()))) (10 () (14 (13 () ()) ()))))

(1 3 4 6 7 8 10 13 14)

Bonus Question

Q 8. Write a lisp function make-cbtree that receives a list, and returns a complete binary tree whose nodes are populated from the elements of the list in the same order.

Examples:

(make-cbtree ’(8 3 10 1))

(8 (3 (1 () ()) ()) (10 () ()))

(make-cbtree ’(8 3 10 1 6))

(8 (3 (1 () ()) (6 () ())) (10 () ()))

Note: In a complete binary tree every level, except possibly the last, is completely lled, and all nodes in the last level are as far left as possible. See 3.

Hint: While both iterative and recursive solutions are acceptable, implementing an iterative solution is recommended. You may use axillary functions to process the list. A sample suggested algorithm is provided in the next page.

The following is a sample iterative algorithm to implement a construction of a complete binary tree.

;; Observe that a tree note is represented by:

;;                   (h () ())

;; There are two placeholders for left and right subtrees.

;; The following algorithm uses a flag called left which ;; indicates that the first empty child is the left one. ;;

;; The algorithm is outlined in the following:

;;

;; 1. initialize root to null, placeholders list to empty, and ;;           left flag to true.

;; 2. if input list is empty return root

;; 3. set root to a newly created node from the head of the

;; input list i.e. (h () ()) where h represents the ;;               first element in the input list.

;; 4. advance the list (set list to the tail of the list)

;; 5. append the root into the placeholders list

;; 6. loop while there are elements to process

;; 6.1. let n be a newly created node from the head of the input

;;                         list (h () ())

;; 6.2. let ph be the first node in the list of place holders

;; 6.3. if left flag is true

;;                                    set the left child in ph to n

;;                   otherwise

;;                                    set the right child in ph to n

;; 6.4. negate the left flag

;; 6.5. if left flag is true (we have consumed both left and right)

;; remove the head node from the placeholders list ;; 6.6. append n to the list of place holders (to the end)

;; 6.7. repeat step 6

;; 7. return root (that is the very first node that was created)

Other solutions may exist.

<h2><a name="_Toc9924"></a>4.2         Procedural Programming with C</h2>

IMPORTANT:                 Make sure the C++ compiler option is turned OFF.

Functions and Pointers

Q 9. Write a function in C that receives an array of integers and returns a pointer to its smallest element. The signature of the function as well as a short code on its usage are given in the following:

int* findmin(int* arr, int size);

int arr[] = {1, 4, 5, 6, -1}; int * m = findmin(arr, 5);

printf(“%d”, *m); // -1

Q 10. You want to write a C library that implements the selection sort to sort an array of integers. The selection sort (6) algorithm is outlined below:

The algorithm divides the input list into two parts: a sorted sublist of items which is built up from left to right at the front (left) of the list and a sublist of the remaining unsorted items that occupy the rest of the list. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list. The algorithm proceeds by nding the smallest element in the unsorted sublist, exchanging (swapping) it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right.

In your implementation, make sure the following requirements are addressed:

<ol>

 <li>The selection sort is implemented in a separate C le with appropriate header</li>

 <li>The selection sort must use the ndmin function, as implemented in the previous question.</li>

 <li>Only the selectionsort function must be exported by the C library. All other de nitions (including ndmin or any other axillary functions) must be kept internal .</li>

 <li>Use the following code to test your implementation.</li>

</ol>

#include “selectionsort.h”

#include “selectionsort.h” // included twice

int arr[] = {1, 4, 5, 6, -1 };

int main() { int i;

selectionsort(arr, 5);

for(i = 0; i &lt; 5; i++) printf(“%d “, arr[i]);

return 0;

}

Q 11. Modify the selection sort function such that it receives a third argument, a pointer to a min function, that is to be called by the sort implementation. In case the pointer is NULL, the default function (the original findmin) is to be called. This will be used in the next question.

Q 12. Write a short program to read an array of <em>n </em>integers, sorts them in both ascending and descending order, and prints the sorted arrays, along with the minimum, maximum, average, and the standard deviation.

Notes:

<ol>

 <li>The array must be dynamically allocated and released upon the termination of theprogram.</li>

 <li>In order to implement the descending order, a pointer to a findmax function must be passed to the sort function.</li>

 <li>The findmax function is to be implemented locally in the main program. The term locally means the function must not be visible outside the code le.</li>

</ol>

LISP lists and the Linked Lists Implementation

Q 13. In this exercise we want to simulate the behaviour of LISP’s list construction in C, where the elements are limited to lists and atoms of char type only.

typedef enum { ATOM, LIST } eltype; typedef char atom; struct _listnode; typedef struct { eltype type; union { atom a; struct _listnode* l;

}; } element; typedef struct _listnode { element el; struct _listnode* next;

} * list;

const element NIL = { .type=LIST, .l=NULL };

<ol>

 <li>Using the above, implement the following functions in C:

  <ol>

   <li>element aasel(atom a); AKA atom as element, returns an element whose content is set to atom <em>a</em>.</li>

   <li>element lasel(list l); AKA list as element, returns an element whose content is set to the list, pointed by <em>l</em>.</li>

   <li>list cons(element e, list l); that creates a new list whose car and cdr are the element <em>e </em>and the list <em>l</em>. While the memory for the newly created list is to be allocated dynamically.</li>

   <li>list append(list l1, list l2); that creates a <u>new </u>list whose elements are shallow copies of elements in <em>l</em>1 and <em>l</em>2, appended.</li>

   <li>element car(element e); that returns head of the list, represented by <em>e</em>; returns NIL, if <em>e </em>is not a list.</li>

   <li>list cdr(element e); that returns tail of the list, represented by <em>e</em>.</li>

   <li>list cddr(element e); that similarly returns the cddr of the list, represented by <em>e</em>.</li>

   <li>void lfree(list l); that frees all the memory previously allocated by the whole list (including all its elements and its inner lists)</li>

   <li>void print(element e); that prints the content of the element <em>e</em>. If <em>e </em>is an atom, it prints the char symbol enclosed in spaces, and if <em>e </em>it is a list, it (recursively) prints the elements of the list enclosed in parentheses (‘(‘ and ‘)’). If <em>e </em>is NIL, the word NIL is printed (see the following example).</li>

  </ol></li>

 <li>Write a short code to create and print the following list:</li>

 <li>Print the car and the cdr of the above list, as well as the car of the car of the original list.</li>

</ol>

The output must look like the following:

( a ( b c ) d e )

a

(( b c ) d e )

NIL

Make sure the list is freed before your program terminates.


