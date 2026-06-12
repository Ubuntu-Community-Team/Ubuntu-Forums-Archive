---
title: "ceiling function"
date: 2009-05-27
forum: General Help
---

### Post by madgod1234 on 2009-05-27
=CEILING(B1;10) returns err:508. same with =CEILING(40731.8;10)

some one pls help

---

### Post by _Purple_ on 2009-05-27
Which language?

---

### Post by indytim on 2009-05-27
There are 3 inputs for the CEILING function:
Number, Significance, and Mode).

I haven't used the function personally, would suggest visiting OO to get more details on the function.   Suspect that the missing "Mode" is causing the errors.

IndyTim

---

### Post by StuartN on 2009-05-27
If you are using OpenOffice Calc then err:508 is a mismatched bracket, which would be in the cell containing the formula rather than the referenced cell.

---

### Post by madgod1234 on 2009-05-27
err:508 is missing bracket.
and mode is optional.
I have not missed the brackets still err function apears.

it is consistent even when I put in a formula insted of value

---

