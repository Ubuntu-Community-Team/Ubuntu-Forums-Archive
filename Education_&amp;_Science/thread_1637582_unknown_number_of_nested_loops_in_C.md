---
title: "unknown number of nested loops in C"
date: 2010-12-04
forum: Education &amp; Science
---

### Post by tekkenlord on 2010-12-04
Hi all,

I am trying to create a C program where I will have "K" nested loops. For example, if K=3, then it would be like this:

for (i=0; i<2; i++) for (j=0; j<2; j++) for (l=0; l<2; l++) {do stuff here};

The problem is I want to use a variable "K" whose value will be given upon execution and will not be known beforehand. Any ideas how to do that? Thanks in advance.

---

### Post by lisati on 2010-12-04
At the moment, I'm inclined to think that some kind of recursive function call might be the answer, with one of the arguments indicating which stage of the "K" levels you're working on.

---

### Post by amauk on 2010-12-04
this really depends on what exactly you're trying to achieve

Does there need to be a single thread of execution,
or could "k = 3" mean that 3 child processes are spawned that work in parallel but do identical things

---

### Post by tekkenlord on 2010-12-04
What I actually need to do, is create a Kx(2^K) matrix whose each column corresponds to a permutation (with replacement) of the set {0,1}. For example, if K=2, the matrix would be

0 0 1 1
1 0 1 0

and for K=3

0 0 0 0 1 1 1 1
0 0 1 1 0 0 1 1
0 1 0 1 0 1 0 1

---

### Post by amauk on 2010-12-04
well, you don't need to do much looping for something like this

if you have 2 possible values (0 or 1)
and 3 sets of values (eg. k = 3)
then the number of possible permutations is
2^k

2^2 = 4
2^3 = 8
2^4 = 16

so you now have the dimensions of your needed 2D array

You'll need the pow() function for raising a number by an exponent
#include <math.h> and link in with -lm

now you just need to populate your array elements with the correct chars (0 or 1)

---

### Post by tekkenlord on 2010-12-05
I think the only possible way is with the recursive function, and I will start with that. Thank you all for your replies.

---

### Post by nice_like_rice on 2010-12-19
So, at the risk of being completely wrong here is my answer.
It's in python but I didn't use any functional programming stuff so it can be easily rewritten in C. 

```

k = 5
matrix = []

for i in range(0,k):
    matrix.append([])
    for poo in range(0,2**k):
        matrix[i].append(0)


```

Just creating a k*2^k matrix.
In C it's just int matrix[k][pow(2,k)];. 

```


jump = 2**k/2

for i in range(0,k):
    j=0
    while j < 2**k:
        for n in range(0,jump):
            if j+n>=2**k:
                break
            matrix[i][j+n]=1
        j=j+2*jump

    
    jump = jump/2


```

Filled the matrix with the values.
Then some silly code to print the matrix :) 
```


for o in range(0,k):
    for p in range(0,2**k):
        print matrix[o][p],

    print ""

```

Output:

```

k=2
1 1 0 0 
1 0 1 0 

k=3
1 1 1 1 0 0 0 0 
1 1 0 0 1 1 0 0 
1 0 1 0 1 0 1 0 

k=4
1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 
1 1 1 1 0 0 0 0 1 1 1 1 0 0 0 0 
1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 
1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0

k=5
1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 
1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 
1 1 1 1 0 0 0 0 1 1 1 1 0 0 0 0 1 1 1 1 0 0 0 0 1 1 1 1 0 0 0 0 
1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 0 
1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0

```

I could be missing something blatantly obvious here :oops:, but that seems to what you were looking for? I just saw a pattern in those first couple of k values.

Hope this is right, I know this post is 2 weeks old!

edit: btw sorry its in python, but think of it as pseudocode lol :) post if you need help writing it in c

---

