---
title: "OpenOffice Calc exclude a range from formula"
date: 2008-12-12
forum: General Help
---

### Post by DBQ on 2008-12-12
Hi everybody.

In open office calc I have a formula to compute something for a range of cells: for example =average(a1:z1).  Suppose that I want to exclude one of the cells from the range.  How I can I do this - I do not want to manually select thousands of cells one by one.

Thank You!

---

### Post by Jim Danner on 2008-12-13
=average(a1:q1,s1:z1)
(Depending on your country settings the , might be a ; )

---

