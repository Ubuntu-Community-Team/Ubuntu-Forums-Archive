---
title: "Cross Product with Maxima/Texmacs"
date: 2008-06-26
forum: Education &amp; Science
---

### Post by bkv2k on 2008-06-26
I'm trying to learn how to do vector math with Maxima. Using command-line or wxMaxima I can do this (cross product):

load(vect);
A : [1,2,3];
B : [4,5,6];
express(A~B);

I get the result: [-3,6,-3].

If I try the same thing using the Texmacs interface I get the result:

AsimB.

Does anyone know how to do a cross product with Texmacs/Maxima?

Thanks

---

### Post by bkv2k on 2008-06-28
Forgive me for answering my own question :-)  I found that turning off the Mathematical Input option in Texmacs solved the problem.  Once this is done
A:[1,2,3]
B:[4,5,6]
express(A~B)
gives
[-3,6,-3]
(cross product of A and B)

---

