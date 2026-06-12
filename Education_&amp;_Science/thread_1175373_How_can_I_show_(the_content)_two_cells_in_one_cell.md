---
title: "How can I show (the content) two cells in one cell in Calc?"
date: 2009-06-01
forum: Education &amp; Science
---

### Post by Gr8world on 2009-06-01
Ok, I hope this is possible...
So what I want is to show the content of two cells in one (after each other). I mean something like this:
if I have two cells:  24
                      25
and what I want to do is to put some kind of formula in an other cell to get this : 2425

Is this possible? Someone knows how to do this? 

And one more thing... It has to be with formula because I have to make a lot of such cells and it is impossible to put it in manually. 



Thanx for reading

---

### Post by samden on 2009-06-01
Try:
```
=CONCATENATE(A1,B1)
```
That is a text command however and you end up with "2425" written as text, not recognised as a number. I am not sure what to do if you want to do further calculations with that number.

---

### Post by Gr8world on 2009-06-01
Yes, it did it! Thanx, and no, I don't have do anything with it later, I just have to store it like that.

thanx

---

### Post by Gr8world on 2009-06-01
Damn, it doesnt work after all...

If I want to drag it and assume that it will recognize and do the same thing, it doesnt. Well here is what I did: 
I had 'n' (n is a regular number) numbers in A1, A2, A3, A4,...,An 
and I wanted to make A1A1 in B1, A1A2 in B2, A1A3 in B3,... so I did =CONCATENATE(A1,A1:An). And it works, but it works only if I put it in manually because when drag e.g. From B1,B2,B3 (already filled in) to e.g. B7
then it doesn't do the right thing, but gives me something like A4A4, A4A5,A4A6, A4A7.

Is there a way to make it work how I want it to work?

---

### Post by Gr8world on 2009-06-01
Ok, maybe another question.... 
Is there a way to copy-paste into a selection of cells? 
for exampple if I select 1000 cells and I put there =CONCATENATE(A1,A1:A1000)
It will work but how can I put this in several cells at once?

---

### Post by gunksta on 2009-06-01
> **Gr8world said:**
> Damn, it doesnt work after all...

If I want to drag it and assume that it will recognize and do the same thing, it doesnt. Well here is what I did: 
I had 'n' (n is a regular number) numbers in A1, A2, A3, A4,...,An 
and I wanted to make A1A1 in B1, A1A2 in B2, A1A3 in B3,... so I did =CONCATENATE(A1,A1:An). And it works, but it works only if I put it in manually because when drag e.g. From B1,B2,B3 (already filled in) to e.g. B7
then it doesn't do the right thing, but gives me something like A4A4, A4A5,A4A6, A4A7.

Is there a way to make it work how I want it to work?


In your first cell, B1, try this. =CONCATENATE($A$1,A1:An)

Now drag. It should work. $ lets you freeze a cell reference in a formula. $A freezes the column while $1 freezes the row.

---

### Post by Gr8world on 2009-06-01
You're genius, thanx.

---

