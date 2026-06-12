---
title: "k3b DVD recognition"
date: 2009-05-26
forum: General Help
---

### Post by texas.chef94 on 2009-05-26
Up to now I have only found it necessary to create live CD on CD RW, so never used DVD capability.
Now I need it and realize I do not have it, but I do in fact have an HL-DT-ST RW/DVD on this machine. Please advise and thank you. Probably not relevant but this is a total linux no MS

Allen

PS
allen@allen-desktop:~$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'HL-DT-ST' 'RW/DVD GCC-4482B'
-------------------------------------------------------------------------
allen@allen-desktop:~$

---

### Post by KhurramM on 2009-05-26
If theres no hardware issue, have u confirmed that it reads DVDs?

---

### Post by logos34 on 2009-05-26
if it's dvd burning you mean, it's possible you're lacking **dvd+rw-tools** pkg (which includes growisofs)

---

### Post by texas.chef94 on 2009-05-26
> **KhurramM said:**
> If theres no hardware issue, have u confirmed that it reads DVDs?

I was under the impression that if it played a DVD then k3b would recognize a blank DVD which it does not. Dumb question I guess is not playing a DVD reading it.

Allen

---

