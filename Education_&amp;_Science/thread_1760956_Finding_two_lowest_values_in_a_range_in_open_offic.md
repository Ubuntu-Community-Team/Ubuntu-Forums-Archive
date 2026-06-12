---
title: "Finding two lowest values in a range in open office calc"
date: 2011-05-17
forum: Education &amp; Science
---

### Post by DBQ on 2011-05-17
Hi Everybody.

Does anybody know of a simple way to find two lowest values in a range in openoffice?  Finding the first value is easy (just use the MIN function).  But what about the second?

P.S. The range may contain duplicates.  I just want to get rid of the two lowest values. For example, if the data is 1 2 2 3, after eliminating the two lowest, the set will be 2 3.

Thank You!

---

### Post by PC_load_letter on 2011-05-17
Use the command SMALL
 the lowest value = SMALL(A1:Z1,1)
2nd lowest value = SMALL(A1:Z1, 2)

I used the range A1:Z1 but you could do it for any range of course.

---

