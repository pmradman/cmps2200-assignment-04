# CMPS 2200 Assignment 4
## Answers

**Name:**___Petra Radmanovic ______






- **1a.**

If each level has d nodes, then at level one there are d children, and at level two there are d^2 children since al;l of the children have d nodes. IF this continues on, the eventual hegiht of the tree is whatever the highest power of d is reached, or d^height. If we compute how many nodes this tree must conbtain, it would be 1 + d + d^2 ... d^height, or (d^h+1 -1 )/d-1. If this is apporximatley the number of nodes, then we can simplify the expressin to say that d^height+1 is about the number of ndoes. Solving for the height gives height= O(log_d n). 
Since each level is filled all the way consecutively, by knowng the mumber of nodes and the pattern the maximum height can be found. 

- **1b.**

For insert, the node is placed to the rightmost leaf, and then swapped with a parent at each level until the tree is restored. This means that at maximum, it compares itself to a parent at each level, or the height of the tree. So, the work to insert would bhe the worst case, or comparing with each level. So W(n) = O(log_d n)

For delete, the node is placed instead of the root and bubbbles downward to restore the heap. This means that it can at maximum, go through every level and potentially be compared with all of the children. since there are d nodes per level of whatever child the node is on, the work would be O( d * log_d n) since at each level, all children comparisons are made. 

- **1c.**

if we change the heap strucure for the algorithm still searching for the shortest path between two nodes, we have to accound for both the insert and delete bounds that were already used. The new heap grows wider, but not as tall as a binary heap. Each edge can cause at most one insert, and each vertex is finalized once. So, in theory there should be max as many inserts as there re edges, and finalized vertices as there are vertices. In this case, our node number is approximately |E|. 

Taking this into account for the way that wewrote the other two bounds, for inserts there are |E| inserts for the work we found for them, or O(|E| log_d |E|), and for the delete operations there are max operations for the work found for delete, or O(d|V| log_d |E|). This is becuase for every delte min which happens |V| times, we compare it to d children for the a maximum comparisons as the ehight of the tree. 

Putting this together, we get O((|E| + d|V|) log_d |E|)

- **1d.**

Given teh above work, we want to find a d assuming |E| = |V|^e + 1 to create the best work. 
If we choose d = |E|/|V|, then we can substtitue the equivalence into the assumption, and they compute to one another. Since our final work was O((|E| + d|V|) log_d |E|), and d|V| = |E|, we get a runtime of approximately |E|. 


- **2a.**

since n-1 = k, k = 2

APSP: (i, j, 2) =  

0.  -2  2
-2. 0.  0
-2. 0   0



- **2b.**

To computete the matrix above, we had to compute it when k = 1 and k = 0 in order to build off of them. This is becuase the shrotest path given how which intermediate vertices can be used builds, so the only differenc between when k = 1 and k = 2 are the paths that are shorter using 2 vertices. The same is true between k = 1 and k = 0. 
To computer k = 2, either we use vertices 2, or the solution is already in k = 1 and k = 0. So APSP(i, j 2) = min(APSP(i,j,1),  APSP(i,2,1), APSP(2,j,1)). we dont need when k = 0 since it is already used for k = 1. 


- **2c.**

APSP(i, j, k) = min(APSP(i,j, k-1),  APSP(i,k,k-1), APSP(k,j,k-1))

- **2d.**
If there are n vertices, there are n choices for each i, j and k. THis gives a total work of n^3 for the first time thw problem is computer. However, once it is stored these problems can be searched in O(1) time, meaning future problems will have a much shorter work. 

- **2e.**

The work of Johnsons algorithm is O(|V||E|log|E|). So, it depends on the values of V and E for when our work of O(|V|^3) for the first run is larger. For graphs with lots of edges, |E| ebcomes very large and can be coparable in terms of |V|, making the overla work larger than |V|^3. So, dynamic programming is best for a graph with lots of edges. 

- **3a.**

An MST automatically wants to avoid heavier edges if a lighter one is an option. Since the MMET wnats to avoid singular heavy edges, if an MST is made iwth the correct choices to be a valid MST, then it automaticlaly made decisions that minimize singular edge weight, also making it an MMET. 

- **3b.**

First, find the actual MST and figure out the total weight of the edges. Then, create an algorithm that computes other possible trees with weights lower than the original MST, and choose the one that has the lowerst weight. 

- **3c.**

First we compute the MST woth W =  O(E log V). Then, for each
of the V−1 edges in that MST the algorithm would remove an edge as to not repeat the MST and see the cost. This would be 
O(E log V) for each edge. Therefore the total work is O(E log V) + V*O(E log V) = O(VE log V)

