---
title: "boolean algebra question"
date: 2010-04-17
forum: Education &amp; Science
---

### Post by fasoulas on 2010-04-17
I don't know if this is the correct place to ask this question,but i will do it

in boolean algebra if i have an expression like this 

AC' + ABC'D

can i simplify it to something like AC + ABD ??

---

### Post by trent.josephsen on 2010-04-19
> **fasoulas said:**
> I don't know if this is the correct place to ask this question,but i will do it

in boolean algebra if i have an expression like this 

AC' + ABC'D

can i simplify it to something like AC + ABD ??

Define "simplify".  In any case the suggested simplification will always be incorrect if C is true and A is false (just as an example); remember C' is the opposite of C.

You can "pull out" the AC' (principle of distribution):
AC' . (1 + BD)

1 + X == 1, so

AC' . (1)

1 . X = X, so

AC'

In other words, the expression AC' + ABC'D is equivalent to just AC'.

---

### Post by fasoulas on 2010-04-20
> **trent.josephsen said:**
> Define "simplify".  In any case the suggested simplification will always be incorrect if C is true and A is false (just as an example); remember C' is the opposite of C.

You can "pull out" the AC' (principle of distribution):
AC' . (1 + BD)

1 + X == 1, so

AC' . (1)

1 . X = X, so

AC'

In other words, the expression AC' + ABC'D is equivalent to just AC'.

what i mean by "simplifing" is we can do something like this 

```
C + C'A
```
is the same as 
```
C + A
```

so..
is this possible ??
```
from  C + BC'D simplified to C + BD
```

the truth tables of the 2 expressions above have the same result

thanks for replying by the way

---

### Post by nateperson on 2010-04-22
If i understand your question and notation, yes.

Its all based off distributivity.  Here's a proof,

C + C'A = C + A:
C union(u) (C' intersect(i) A) equals(=) C union(u) A

so C u (C' i A) = (C u C') i ( C u A) 
now 
C u C' = 1 
so
1 i (C u A) = C u A

so expanding the principal,

 C + BC'D  = C u (B i C' i D)

=(C u (B i C')) i (C u (B i D)) i (C u (C' i D)
=(C u B) i (C u (B i D)) i (C u D)
= (C u (B i D)) i (C u (B i D))
= (C u (B i D)
= C + BD

---

### Post by fasoulas on 2010-04-22
> **nateperson said:**
> If i understand your question and notation, yes.

Its all based off distributivity.  Here's a proof,

C + C'A = C + A:
C union(u) (C' intersect(i) A) equals(=) C union(u) A

so C u (C' i A) = (C u C') i ( C u A) 
now 
C u C' = 1 
so
1 i (C u A) = C u A

so expanding the principal,

 C + BC'D  = C u (B i C' i D)

=(C u (B i C')) i (C u (B i D)) i (C u (C' i D)
=(C u B) i (C u (B i D)) i (C u D)
= (C u (B i D)) i (C u (B i D))
= (C u (B i D)
= C + BD

although i can't really understand your explanation because i am a beginner thanks for proving it,

---

### Post by Azrael3000 on 2010-04-23
nateperson's proof is of course correct. to illustrate it I suggest you draw some example sets and look what the equations actually mean when you draw them.

---

