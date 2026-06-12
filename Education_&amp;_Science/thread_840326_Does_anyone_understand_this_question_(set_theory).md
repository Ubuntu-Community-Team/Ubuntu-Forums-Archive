---
title: "Does anyone understand this question? (set theory)"
date: 2008-06-25
forum: Education &amp; Science
---

### Post by ProbablyX on 2008-06-25
Hello!

I'm trying to solve this problem:
> 
The set A = {1, 3, 5}. How many relations are there on A?


I've tried to mix {1,3} {1,5} and count them, that's not right.
I've tried taking 2^3 (a formulae that isnt helping either)
I've tried to mix {1,3} {1,5}, but remove the dublicates like {3,1} - no luck there either.
I've tried many other approaches also, but I've failed.

The general issue here is that I don't really understand what they're after, lol. The question is kinda... "open". I would ask my math professor but he's on vacation it seems.. lol.

Could anyone help me get any idea what the question really means? lol

Thanks!

---

### Post by karasuman on 2008-06-25
Usually, a question like this is asking for binary relations, in which case you'd have the ordered pairs (1,3), (1,5), (3,1), (3,5), (5,1), (5.3) and possibly (1,1), (3,3), and (5,5) depending on whether an element can act upon itself.

Does that help?  I agree that this is a pretty vague question.  Are there any clues from examples in the text?

---

### Post by WW on 2008-06-25
What do you mean when you say the different answers you tried "failed"?


It seems to me that you have to first understand what a *relation* is.  Wikipedia has [this article](http://en.wikipedia.org/wiki/Relation_(mathematics)).  If we start with that definition, we still have know what order of relation to consider. Binary? Unary? etc.  Or perhaps the question is to give the total number of possible relations of any order?

Let's start with binary relations.  You can think of a binary relation as a table, with each row and each column corresponding to an element of the set.  Here, for example, is a relation on your set (this is the "equality" relation):
```

    1  3  5
   --------
1 | T  F  F
3 | F  T  F 
5 | F  F  T

```
Note that there are 9 elements in the table, each either True or False.

Any assignment of logical values to that 3x3 table defines a binary relation.  This should be enough of a hint for you to figure out the total number of possible binary relations.

---

### Post by ProbablyX on 2008-06-26
Thanks :) I'll try that.

> **WW said:**
> What do you mean when you say the different answers you tried "failed"?
The question is from a self-test after a chapter in the math/logic book. Like "did you get it" test you can try online.
That's why it's so annoying that I can't get any more info on what they're after =/. 
It only tells you "right" or "wrong" :P (You can try any amount of times until you get it right). Kinda to test yourself so that you can solve real problems, instead of just using the mathbook where you can check your results yourself.

---

### Post by ProbablyX on 2008-06-29
> **WW said:**
> 
```

    1  3  5
   --------
1 | T  F  F
3 | F  T  F 
5 | F  F  T

```
Note that there are 9 elements in the table, each either True or False

9 is wrong and so is 6. I tried those initially =/


> 
oh!!!!!!!!!!!!! mathematics
hey what you are doing? studying or doing something, 


I'm studying, this is a self-test after a set theory chapter in the math book. :)

---

### Post by WW on 2008-06-29
> **ProbablyX said:**
> 9 is wrong and so is 6. I tried those initially =/

The table has nine elements, each of which can be True or False.  How many different ways can you fill in the table with T/F values?

Consider the similar question: a "byte" is an 8 bit binary number; each bit can be either 0 or 1.  How many numbers can be represented with a byte?

---

### Post by ProbablyX on 2008-06-29
> **WW said:**
> The table has nine elements, each of which can be True or False.  How many different ways can you fill in the table with T/F values?

Consider the similar question: a "byte" is an 8 bit binary number; each bit can be either 0 or 1.  How many numbers can be represented with a byte?


If I understand you right we'd get 3^8 = 729, but that isnt right...

The T/F list would make 18 which isnt right either. I got 36 in a calculation I made here now too but that isnt right either... lol

Thanks for helping :)

What I was thinking of is maybe that they want to know how many subsets can be created of {1, 3, 5}
Like we have {1,3} {1,5} {3,1} {3,5} {5,1} {5,3} {{1,3} {1,5}} or sumt... but that seems wrong too :S

---

### Post by WW on 2008-06-29
> **ProbablyX said:**
> If I understand you right we'd get 3^8 = 729, but that isnt right...

Why 3^8?


Here's a different example.

Suppose instead that you had just two elements in the set, say {1,3}.  Then the table would be 2x2.  Here are all the possible binary relations:
```

  1 3      1 3      1 3      1 3
1 F F    1 T F    1 F T    1 T T
3 F F    3 F F    3 F F    3 F F

  1 3      1 3      1 3      1 3
1 F F    1 T F    1 F T    1 T T
3 T F    3 T F    3 T F    3 T F

  1 3      1 3      1 3      1 3
1 F F    1 T F    1 F T    1 T T
3 F T    3 F T    3 F T    3 F T

  1 3      1 3      1 3      1 3
1 F F    1 T F    1 F T    1 T T
3 T T    3 T T    3 T T    3 T T

```
In this case, there are 16 possible binary relations.

---

### Post by RebounD11 on 2008-06-30
I'd say they were 2^9... nine values, each being either T or F... but it's just another guess. :D

---

### Post by ProbablyX on 2008-06-30
> **RebounD11 said:**
> I'd say they were 2^9... nine values, each being either T or F... but it's just another guess. :D

A very good guess :D 512 was right :)

So I suppose if you have {a,b,c} you do this:
a,b a,c a,a
b,a b,c b,b
c,a c,b c,c

count them = 9 and then 2^9 instead of 2^3? =)

Thanks :D

---

### Post by WW on 2008-06-30
Right.  More generally, if you have a set of N elements, the number of possible binary relations is 2^(N^2).

---

### Post by RebounD11 on 2008-07-02
> **ProbablyX said:**
> A very good guess :D 512 was right :)

So I suppose if you have {a,b,c} you do this:
a,b a,c a,a
b,a b,c b,b
c,a c,b c,c

count them = 9 and then 2^9 instead of 2^3? =)

Thanks :D

You're welcome! WW put it more generally and better explained.

---

### Post by bapoumba on 2008-07-06
Is this some kind of home assignment ?
Sorry for the late notice, this thread just got reported.
[QUOTE=UF CoC - Section II.6]While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.[/QUOTE]

---

