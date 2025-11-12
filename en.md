# Linear Algebra in A Nutshell

## Table of Contents

[TOC]

## Elementary Row Manipulations

- $\mathrm R_i \leftrightarrow \mathrm R_j$
- $\mathrm R_i \gets \mathrm R_i + c$
- $\mathrm R_i \gets \mathrm R_i + {\color{blue}c\mathrm R_j}$
  - This implies $\mathrm R_i \gets c\mathrm R_i$ is also an elementary row manipulation. 


Which equals to

- adding linear combinations of some rows to itself
  $$
  \mathrm R_i \gets \mathrm R_i + \left(\sum c_j \mathrm R_j\right)
  $$

- changing the sequence of rows

> [!Note]
>
> Elementary row manipulations are **reversible**. In fact, there exists inversible matrixes $E$ such that left-multiplying them to $A$ equals to doing elementary row manipulations on $A$. 
> $$
> A \sim EA
> $$

## Reducing to ref & rref

TL;DR, 

- Row Echelon Form (ref)
  - is the shape of an echelon & rows with all $0$ in the bottom of the matrix
  - **all elements under each pivot are $0$**
- Reduced Row Echelon Form (rref):
  - is ref
  - each pivot equals to $1$
  - **all elements above each pivot are $0$**

## Parametric Vector Form

1. Reduce to rref.
2. Construct vector $\boldsymbol x = \begin{pmatrix}x_1 & x_2 & \cdots & x_n\end{pmatrix}^\mathsf T$.
3. Substitute pivots in $\boldsymbol x$ into linear combinations of non-pivots according to rref.
4. Write PVF
   - Parameters in PVF are non-pivots in $A$ 
   - $\dim N (A) =\text{\# vectors in PVF} = \operatorname{nullity} A$

## Matrix Algebra

### Add, Scalar Multiplication, Multipliction

Some simple math. 

Note that for **diagional matrixes** $A = (a_i)$ and $B = (b_i)$, $AB = (a_ib_i)$. 

### (Multiplicational) Inverse

$$
AA^{-1} = A^{-1}A = I
$$

Finding $A^{-1}$:
$$
(A|I) \sim (EA|A) \Rightarrow E = A^{-1}
$$

### Determinants (tool to determine existence of inverse)

#### *Row manipulations on $A$ results in the following changes in $\det A$*

- $\mathrm R_i \leftrightarrow \mathrm R_j$ : $\det A$ changes to $-\det A$
- $\mathrm R_i \gets c\mathrm R_i$ : $\det A$ changes to ${\color{blue}c}\det A$
  - $\det (cA) = {\color{blue}c^m} \det A$
- $\mathrm R_i \gets \mathrm R_i + c\mathrm R_j$ : $\det A$ doesn't change

#### *Calculating $\det$*

$$
\det A = \sum_{\text{expand by any row/column}} a_{ij}C_{ij}
$$

where $C_{ij}$ is **cofactor** of $A$, $\boxed {C_{ij} = (-1)^{i + j}M_{ij}}$, and $M_{ij}$ is the **minor** of $A$. 

#### *More properties*

- $\det A^\mathsf T = \det A$
- det of diagonal matrixes = product of elements on diagonals.

#### *Applications of determinants*

- Finding areas of polygons
  
- Solving Linear Systems (Cramer's Rule)

  - $$
    x_i = \frac{\det A_i(\boldsymbol b)}{\det A}
    $$
    where $\det A_i(\boldsymbol b)$ is substituting $i$-th column of $A$ with $\boldsymbol b$. 

- Finding inverse of matrix
  $$
  A^{-1} = \frac{\operatorname{adj} A}{\det A}
  $$
  Where **adjoint matrix** $\operatorname{adj}A = C^\mathsf T$ is the transpose of cofactors of $A$. 

- Calculating Cross Products (in $\R^3$ space)
  $$
  \boldsymbol v_1 \times \boldsymbol v_2 = \left|\begin{matrix}
  \hat{\boldsymbol{i}} & \hat{\boldsymbol{j}} & \hat{\boldsymbol{k}}\\
  v_{1x} & v_{1y} & v_{1z} \\
  v_{2x} & v_{2y} & v_{2z}
  \end{matrix}\right|
  $$

- 

### Inverse of $2\times 2$ Matrixes

$$
\begin{pmatrix}
a & b \\ c & d
\end{pmatrix}^{-1}
=
\frac{1}{ad-bc}
\begin{pmatrix}
d & -b \\ -c & a 
\end{pmatrix}
$$



### Transpose and Symmetry

Transpose is exchanging rows and columns, which denotes as $A^\mathsf T$. 

### Rank

Equivalent definitions 

- $\operatorname{rank} A$
- $\dim C(A)$
- maxium \# of L.I. row vectors or column vectors in $A$
- \# pivots in rref $(A)$

## Linear Combination

Linear Combination (abbreviated as L.C. in this cheat sheet) is defined by
$$
\sum c_i \boldsymbol v_i\quad (c_i \in \R)
$$

## Linear Space

Linear space, a.k.a. vector space are spaces defined by $(V, +, \cdot)$. Note that this notation implies closure of add and scalar multiplication on $V$. 

One of the important properties of linear space is: $\boldsymbol 0 \in V$.
$$
0 \in \R, \boldsymbol v \in V, 0\boldsymbol v \in V \Rightarrow  \boldsymbol 0 \in V
$$

One of the important subspaces is $\{\boldsymbol 0\}$, which is space spanned by the only vector $\boldsymbol 0$. 

### Linear Subspace

Substucture of linear space. 

> [!Tip]
>
> To check whether $X$ is subspace of some given $V$ (or $\mathbb R^m$), check whether 
>
> - $\boldsymbol 0 \in X$?
> - add closure on $X$?
> - scalar multiplication closure on $X$?

### Linear Independence

For a set of vectors, if the only solution to the equation
$$
\sum c_i\boldsymbol v_i = \boldsymbol 0
$$
is 
$$
\forall c_i = 0
$$
then the set is **linear independent**. Otherwise, the set is **linear dependent** (i.e. L.C. of some vectors in the set can be expressed by L.C. of other vectors in the set). 

> [!Tip]
>
> Sets containing $\boldsymbol 0$ are all linear dependent, because $\boldsymbol 0$ can be expressed by $0$ times any vector (such a trivial example of linear combination)! 

### Span

Span is the linear space containing all L.C.'s of the spanning set.

### Dimension

Minimum # of vectors spanning the vector space. ($\Leftrightarrow$ Maximum # of L.I. vectors in the spanning set)

### Basis and Coordinates

Basis is a list of L.I. vectors that spans the whole vector space.
$$
\text{\# basis of $V$} = \dim V
$$

## Fundamental Spaces of Matrixes

### Column Space $C(A)$

Space spanned by column vectors of $A$.

 ### Null Space $N(A)$

Linear space that contains all solution to $A\boldsymbol x = \boldsymbol 0$. 

### Row Space $C\left(A^\mathsf T\right)$

### Null Space of Transpose $N \left(A^\mathsf T\right)$

### Theorems Related to Fundamental Spaces

- **Fundamental Theorem of Linear Algebra**. 
- **The Invertible Matrix Theorem**. 

### \* Verifying Answers Using Computer Algebra System

``` python
from sympy import *

A = Matrix([
    [0, 1, 2, 3, 4], 
    [0, 1, 2, 4, 6], 
    [0, 0, 0, 1, 2]
])

B = Matrix([
    [1, 2, 3, 4],
    [6, 13, 20, 27],
    [9, 26, 44, 62]
])

def four_spaces(X: Matrix):
    return [X.columnspace(), X.nullspace(), X.transpose().columnspace(), X.transpose().nullspace()]
  
names = ['C(X)', 'N(X)', 'C(X^T)', 'N(X^T)']
spaces = four_spaces(A)
for i, name in enumerate(names):
    print(f'{name}:\n {spaces[i]}\n\n') 
```

## \* Linear Transformation

*(\*: Not required on midterm.)*

- $T(\boldsymbol x+\boldsymbol y) = T(\boldsymbol x) + T(\boldsymbol y)$
- $T(c\boldsymbol x) = cT(\boldsymbol x)$
  - which implies $T(\boldsymbol 0) = \boldsymbol 0$. 

## Linear Systems

### Solutions

- no solution
- infinity many solutions
- exactly one solution
