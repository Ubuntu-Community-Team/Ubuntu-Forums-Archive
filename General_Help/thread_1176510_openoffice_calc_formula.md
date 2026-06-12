---
title: "openoffice calc formula"
date: 2009-06-02
forum: General Help
---

### Post by Woody1987 on 2009-06-02
Im writing a basic formula in which the row number has to be a value derived from another cell. The basic formula is 

> =AVERAGE(c5)

but what i want is for the 5 to be for example e6+1 where the value of e6 is 4, so essentially my formula needs to be somethng like 

> =AVERAGE(c(e6+1)) 
so e6 (value of 4) + 1 equals 5 so we get c5 like the first formula, but this doesnt work. Is what i want possible?

---

### Post by Woody1987 on 2009-06-02
nevermind i solved it

=AVERAGE(C6:INDIRECT("C"&E6))

how do i mark this as solved?

---

