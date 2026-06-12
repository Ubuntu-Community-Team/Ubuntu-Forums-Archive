---
title: "Array size in Octave"
date: 2009-05-12
forum: Education &amp; Science
---

### Post by in_flu_ence on 2009-05-12
Anyone know what is the maximum size that an array can take in octave?

I have 120000 values wanting to put in an array
when I did so, I found that I can only get 100000?

what I did is 

M=dlmread('test.csv','','a1..a120000')
mlen=length(M) %This shows 100000

Any advice?

---

### Post by in_flu_ence on 2009-05-14
Apparently no one responded but this does appear that I can only have 100K elements in an array within Octave. After trying to put my script with 100K elements and 100001 elements, both gives a length of 100K.

Hope someone will pick up the point and keep posted although not a ubuntu issue after all.

---

### Post by jpkotta on 2009-05-15
It probably has something to do with your file or the import function (what is dlmread() from?).  Octave should no trouble with arrays of several million elements.

---

