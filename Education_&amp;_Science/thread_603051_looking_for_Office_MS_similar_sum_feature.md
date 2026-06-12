---
title: "looking for Office MS similar sum feature"
date: 2007-11-04
forum: Education &amp; Science
---

### Post by ub9876 on 2007-11-04
looking for a tool that adds all the numbers that are highlighted in a row. Open Office doesnt do this well. for ubu. any ideas??

---

### Post by Zugzwang on 2007-11-05
Don't Know of any. Maybe you can create an extra row in which you add the information if the cell above is selected or not and use the SUMIF function?

In OpenOffice, for example, you type the number into the cells A1...E1 and the information whether the cells are selected or not into A2...E2. Then you can use the formula "=SUMIF(A2:E2;">" & 0;A1:E1)" to get the conditional sum as requested.

---

