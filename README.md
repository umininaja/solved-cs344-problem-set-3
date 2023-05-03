Download Link: https://assignmentchef.com/product/solved-cs344-problem-set-3
<br>
<strong>Drawing graphs: </strong>You might try http://madebyevan.com/fsm/ which allows you to draw graphs with your mouse and convert it into L<sup>A</sup>TEXcode:

You can also draw by hand and insert a picture.

<strong>Make best use of picture in Latex</strong>: If you think some part of your answer is too difficult to type using Latex, you may write that part on paper and scan it as a picture, and then insert that part into Latex as a picture, and finally Latex will compile the picture into the final PDF output. This will make things easier. For instructions of how to insert pictures in Latex, you may refer to the Latex file of our homework 1, which includes several examples of inserting pictures in Latex.

Discussion Group (People with whom you discussed ideas used in your answers if any): Xudong Jiang

I acknowledge and accept the Honor Code. Please type your initials below: <strong>Signed</strong>: (YC)

<ol>

 <li><strong>Warmup with DFS/BFS. </strong>(20 points)

  <ul>

   <li>Give one example of a directed graph on four vertices, <em>A</em>, <em>B</em>, <em>C</em>, and <em>D</em>, such that both depth-first search and breadth-first search discover the vertices in the same order when started at A.</li>

  </ul></li>

</ol>

Answer: When DFS started at A, recover vertices in order ABCD. When BFS started at A, also recover vertices in order ABCD.

Figure 1: Question 1(a).

<ul>

 <li>Give one example of a directed graph where DFS and BFS discover the vertices in a different order when started at <em>A</em>.</li>

</ul>

Figure 2: Question 1(b).

Answer: DFS started at A discovers vertices in order ABCD. BFS started at A does it in order ABCD.

“Discover” means the time that the algorithm first reaches the vertex, referred to as start_time during lecture. Assume that both DFS and BFS iterate over outgoing neighbors in alphabetical order.

<strong>[We are expecting a drawing of your graphs and an ordered list of vertices discovered by DFS and BFS.]</strong>

<ol start="2">

 <li><strong>Warmup with Dijkstra. </strong>(20 points)</li>

</ol>

Let <em>G </em>= (<em>V,E</em>) be a weighted directed graph. For the rest of this problem, assume that <em>s,t </em>∈ <em>V </em>and that <strong>there exists a directed path from </strong><em>s </em><strong>to </strong><em>t</em>.

For the rest of this problem, refer to the implementation of Dijkstra’s algorithm given by the pseudocode below.

dijkstra_st_path(G, s, t):

for all v in V, set d[v] = Infinity for all v in V, set p[v] = None

// we will use p to reconstruct the shortest s-t path at the end d[s] = 0

F = V D = []

while F isn’t empty:

x = vertex v in F such that d[v] is minimized for y in x.outgoing_neighbors:

d[y] = min( d[y], d[x] + weight(x,y) ) if d[y] was changed in the previous line, set p[y] = x

F.remove(x)

D.add(x)

// use p to reconstruct the shortest s-t path path = [t] current = t while current != s: current = p[current] add current to the front of the path

return path, d[t]

The variable p maintains the “<strong>p</strong>arents” of the vertices in the shortest s-t path, so it can be reconstructed at the end.

Step through dijkstra st path(<em>G,s,t</em>) on the graph <em>G </em>shown below. Complete the table below to show what the arrays d and p are at each step of the algorithm, and indicate what path is returned and what its cost is.

<strong>[We are expecting the table below filled out, as well as the final shortest path and its cost. No further justification is required.]</strong>

<table width="613">

 <tbody>

  <tr>

   <td width="244"> </td>

   <td width="41">d[<em>s</em>]</td>

   <td width="42">d[<em>u</em>]</td>

   <td width="41">d[<em>v</em>]</td>

   <td width="40">d[<em>t</em>]</td>

   <td width="52">p[<em>s</em>]</td>

   <td width="51">p[<em>u</em>]</td>

   <td width="51">p[<em>v</em>]</td>

   <td width="51">p[<em>t</em>]</td>

  </tr>

  <tr>

   <td width="244">When entering the first while loop for the first time, the state is:</td>

   <td width="41">0</td>

   <td width="42">∞</td>

   <td width="41">∞</td>

   <td width="40">∞</td>

   <td width="52">None</td>

   <td width="51">None</td>

   <td width="51">None</td>

   <td width="51">None</td>

  </tr>

  <tr>

   <td width="244">Immediately after the first element of <em>D </em>is added, the state is:</td>

   <td width="41">0</td>

   <td width="42">3</td>

   <td width="41">∞</td>

   <td width="40">∞</td>

   <td width="52">None</td>

   <td width="51">s</td>

   <td width="51">None</td>

   <td width="51">None</td>

  </tr>

  <tr>

   <td width="244">Immediately after the second element of <em>D </em>is added, the state is:</td>

   <td width="41">0</td>

   <td width="42">3</td>

   <td width="41">5</td>

   <td width="40">7</td>

   <td width="52">None</td>

   <td width="51">s</td>

   <td width="51">u</td>

   <td width="51">u</td>

  </tr>

  <tr>

   <td width="244">Immediately after the third element of <em>D </em>is added, the state is:</td>

   <td width="41">0</td>

   <td width="42">3</td>

   <td width="41">5</td>

   <td width="40">6</td>

   <td width="52">None</td>

   <td width="51">s</td>

   <td width="51">u</td>

   <td width="51">v</td>

  </tr>

  <tr>

   <td width="244">Immediately after the fourth element of <em>D </em>is added, the state is:</td>

   <td width="41">0</td>

   <td width="42">3</td>

   <td width="41">5</td>

   <td width="40">6</td>

   <td width="52">None</td>

   <td width="51">s</td>

   <td width="51">u</td>

   <td width="51">v</td>

  </tr>

 </tbody>

</table>

The final shortest path returned is <em>s </em>→ <em>u </em>→ <em>v </em>→ <em>t</em>, the cost is <em>d</em>[<em>t</em>] = 6.

<ol start="3">

 <li><strong>Fun with Reductions. </strong>(15 points) Suppose the economies of the world use a set of currencies <em>C</em><sub>1</sub><em>,…,C<sub>n</sub></em>; think of these as dollars, pounds, Bitcoin, etc. Your bank allows you to trade each currency <em>C<sub>i </sub></em>for any other currency <em>C<sub>j</sub></em>, and finds some way to charge you for this service. Suppose that for each ordered pair of currencies (<em>C<sub>i</sub>,C<sub>j</sub></em>), the bank charges a flat fee of <em>f<sub>ij </sub>&gt; </em>0 dollars to exchange <em>C<sub>i </sub></em>for <em>C<sub>j </sub></em>(regardless of the quantity of currency being exchanged).</li>

</ol>

Describe an algorithm which, given a starting currency <em>C<sub>s</sub></em>, a target currency <em>C<sub>t</sub></em>, and a list of fees <em>f<sub>ij </sub></em>for all <em>i,j </em>∈ {1<em>,…,n</em>}, computes the cheapest way (that is, incurring the least in fees) to exchange all of our currency in <em>C<sub>s </sub></em>into currency <em>C<sub>t</sub></em>. Also, justify the its runtime.

<strong>[We are expecting a description or pseudocode (either is OK) of your algorithm, as well as a brief justification of its runtime. You can use any algorithm we have learned in class.]</strong>

Answer: According to the question we know that we have n currencies, and we must convert from one currency to another currency, A fixed fee will be charged every time you exchanged in your banks. So we basically need to take measures to minimize the cost. This is basically a problem with the shortest path algorithm. We can use Dijkstra Algorithm to solve.

let Q is a queue of all nodes in the graph. when the algorithm’s progress end, Q would be empty.S is an empty set to indicate which nodes the algorithm has visited. when the algorithm’s run end, S would contain all the nodes of the graph. Vertices denoted by v, nodes denoted by u.

Pseudocode:

Dijkstra(Graph, currency) distant[currency] := 0; for (each vertex v in Graph) if (v currency) distant[v] := infinity;

add v to Q;

endif; endfor;

while (Q is not empty) v := vertex in Q with min distant[v]; remove v from Q; for (each neighbor u of v ) alt := distant[v] + length(v, u); if (alt ¡ distant[u]) distant[u] := alt ; endif; endfor; return distant[]; endwhile;

The cost of a path between two vertices in G is the sum of the weights of the vertices on that path. We show that, for such graphs, the time complexity of Dijkstra’s algorithm, implemented with a binary heap, the runtime is <em>O</em>(|<em>E</em>| + |<em>V </em>|<em>log</em>|<em>V </em>|).

<ol start="4">

 <li><strong>Social engineering. </strong>(15 points + 10 bonus points)</li>

</ol>

Suppose we have a community of <em>n </em>people. We can create a directed graph from this community as follows: the vertices are people, and there is a directed edge from person <em>A </em>to person <em>B </em>if <em>A </em>would forward a rumor to <em>B</em>. Assume that if there is an edge from <em>A </em>to <em>B</em>, then <em>A </em>will always forward any rumor they hear to <em>B</em>. Notice that this relationship isn’t symmetric: <em>A </em>might gossip to <em>B </em>but not vice versa. Suppose there are <em>m </em>directed edges total, so <em>G </em>= (<em>V,E</em>) is a graph with <em>n </em>vertices and <em>m </em>edges.

Define a person <em>P </em>to be <em>influential </em>if for all other people <em>A </em>in the community, there is a directed path from <em>P </em>to <em>A </em>in <em>G</em>. Thus, if you tell a rumor to an influential person <em>P</em>, eventually the rumor will reach everybody. You have a rumor that you’d like to spread, but you don’t have time to tell more than one person, so you’d like to find an influential person to tell the rumor to.

In the following questions, assume that <em>G </em>is the directed graph representing the community, and that you have access to <em>G </em>as an array of adjacency lists: for each vertex <em>v</em>, in <em>O</em>(1) time you can get a pointer to the head of the linked lists <em>v</em>.outgoing neighbors and <em>v</em>.incoming neighbors. Notice that <em>G </em>is not necessarily acyclic. In your answers, you may appeal to any statements we have seen in class, in the notes, or in CLRS.

<ul>

 <li>(15 points) Show that all influential people in <em>G </em>are in the same strongly connected component, and that everyone in this strongly connected component is influential.</li>

</ul>

<strong>[Hint: You need to refer the definition of strongly connected component, and you can prove using either induction or contradiction.]</strong>

Answer:If v and v’ are influential, there is a path from v to V’ and from v’ to v. Therefore, according to the definition, v and v’ are in the same strongly connected component. As same, if v is influential and v’ is in the same SCC as v, v’ is influential. because there is a path from v’ to v to u, for all u ∈ <em>V.</em>

<ul>

 <li>(10 bonus points) Suppose that an influential person exists. Give an algorithm that, given <em>G</em>, finds an influential person.</li>

</ul>

<strong>[We are expecting a description or pseudocode of your algorithm and a short argument about the runtime. You can borrow any algorithm that we have learned in class.] </strong>Answer: Pseudocode:

influentialPerson(G) L=v; <strong>while </strong>(L is not empty) v = any vertex in L;

VISTED = [];

DFStruncated (VISITED, <em>L</em>, <em>v</em>); remove all the vertices in VISITED from L; <strong>return v</strong>; endwhile;

DFStruncated(VISITED, L, s)

<strong>if</strong>(<em>s </em>== <em>NULL </em>—— <em>s </em>is not in L)

<strong>return</strong>; endif;

VISITED.add(s); <strong>for </strong>(<em>v </em>in s.neighbors) DFStruncated(VISITED, L, v); endfor;

In all DFStruncated calls, each vertex is only added to one VISITED, because once it has been visited in a call of DFStruncated, it is added to VISITED and subtracted from L; it will never be DFStruncated access. Since DFStruncated only traverses directed adges(u, v), if it add u to the VISITED, it means that each directed edge is traversed only once. Therefore, the runtime is O(m+n).

<ol start="5">

 <li><strong>Job Sequencing Problem. </strong>(15 points)</li>

</ol>

In this problem we have <em>n </em>jobs <em>j</em><sub>1</sub><em>,j</em><sub>2</sub><em>,…,j<sub>n</sub></em>, each has an associated deadline <em>d</em><sub>1</sub><em>,d</em><sub>2</sub><em>,…,d<sub>n </sub></em>and profit <em>p</em><sub>1</sub><em>,p</em><sub>2</sub><em>,…,p<sub>n</sub></em>. Profit will only be awarded or earned if the job is completed before the deadline. We assume that each job takes 1 unit of time to complete. The objective is to earn maximum profit when only one job can be scheduled or processed at any given time.

Describe or provide the pseudocode of an algorithm to find the sequence of jobs to do with the maximum total profit.

<strong>[Hint: You can select the jobs in a greedy way. You can use the following example to help your analysis.]</strong>

<table width="242">

 <tbody>

  <tr>

   <td width="76">Job</td>

   <td width="32">J1</td>

   <td width="39">J2</td>

   <td width="32">J3</td>

   <td width="32">J4</td>

   <td width="32">J5</td>

  </tr>

  <tr>

   <td width="76">Deadline</td>

   <td width="32">2</td>

   <td width="39">1</td>

   <td width="32">3</td>

   <td width="32">2</td>

   <td width="32">1</td>

  </tr>

  <tr>

   <td width="76">Profit</td>

   <td width="32">60</td>

   <td width="39">100</td>

   <td width="32">20</td>

   <td width="32">40</td>

   <td width="32">20</td>

  </tr>

 </tbody>

</table>

The best job sequence would be <em>J</em>2 → <em>J</em>1 → <em>J</em>3.

Answer:

For this question, If we look at job j2, it has a deadline 1. This means we have to complete job j2 in time slot 1 if we want to earn its profit.As same, if we look at job j1 it has a deadline 2. This means we have to complete job j1 on or before time slot 2 in order to earn its profit.

Pscudocode:

<strong>for </strong>(<em>i </em>= 1; <em>i &lt;</em>= <em>n</em>, <em>i </em>+ +) do

Set j = min(deadlineMax, Deadline(i)); <strong>while </strong><em>j &gt;</em>= 1 do

<strong>if </strong>(timeSlot[j] is EMPTY) timeSlot[j] = Job(i); <strong>break</strong>;

endif;

Set j = j – 1;

endwhile; endfor;

<ol start="6">

 <li><strong>Alternative Minimum Spanning Trees (23.4 CLRS). </strong>(15 points + 10 bonus points) In this problem, we give pseudocode for two different algorithms. Each one takes a connected graph and a weight function as input and returns a set of edges T. For each algorithm, either show that T is a minimum spanning tree (give a brief justification of the algorithm) or show that T is not a minimum spanning tree (give a counter-example).</li>

 <li>(15 points) <strong>MAYBE-MST-A </strong>(<em>G,w</em>)

  <ol>

   <li>sort the edges into non-increasing order of edge weights <em>w</em></li>

   <li><em>T </em>= <em>E</em></li>

   <li>for each edge <em>e </em>∈ <em>E</em>, taken in non-increasing order by weight</li>

   <li>if <em>T </em>− {<em>e</em>} is a connected graph</li>

   <li><em>T </em>= <em>T </em>− {<em>e</em>}</li>

   <li>return <em>T</em></li>

  </ol></li>

</ol>

Answer: MAYBE-MST-A is a MST algorithm. As we know that we cannot remove an edge that must be part of a minimum spanning tree. so we cannot remove e that is a bridge. We only remove an edge e if T-e is a connected graph and e lies on a simple cycle of the graph. Since we remove edges in non-increasing order, the weight of every edge on the cycle must be less than or equal to e. so the output T is composed of a minimum number of edges of minimum weight, and is valid MST. This is a minimum spanning tree on G with edge e removed.

<ol>

 <li>(10 bonus points) <strong>MAYBE-MST-B </strong>(<em>G,w</em>)</li>

</ol>

<ol>

 <li><em>T </em>= <em>null</em></li>

 <li>for each edge <em>e</em>, taken in arbitrary order</li>

 <li>if <em>T </em>∪ {<em>e</em>} has no cycles</li>

 <li><em>T </em>= <em>T </em>∪ {<em>e</em>}</li>

 <li>return <em>T</em></li>

</ol>

Answer: MAYBE-MST-B is not a MST algorithm. If the algorithm examines the edges in their order listed, the algorithm never adjusts edges or removes edges. Because of the arbitrary order. We could add any edge e to the MST. The heavy edge did not make a cycle when lighter edges would be more optimal. For example, let G be the graph on 3 vertices a, b, and c. The edges be (a,b)with weights 3. The edges be (b,c)with weights 2, The edges be (c,a)with weights 1. So it would take the two heaviest edges when the algorithm examines the edges in their order listed. T is not a minimum spanning tree.