---
title: "location of the directory of C header files ???"
date: 2006-06-23
forum: Desktop Environments
---

### Post by muzaki on 2006-06-23
What is the location of the directory of C header files that match my running
kernel? (i am running 2.6.15-25) 
it should be here [/usr/src/linux/include], but i cant find it???
please  immediate help needed


-------
EDIT: found the solution. Please ignore this

---

### Post by chrestomanci on 2006-06-23
You need to install the kernel headers package to match your currently installed kernel

---

### Post by yanqui on 2008-05-29
I realize this is an old thread, but exactly HOW does one do that?

---

### Post by Marthr on 2008-06-10
I hope you already found the solution yanqui, but if you didn't: here's the explanation.

You should jump into the terminal and look for the version of your kernel:

$ uname -r

Then you can use the package manager:

$ sudo apt-get install linux-headers-"uname -r"

Ofcourse you fill in the generated kernel version for "uname -r"
Hope I helped you or maybe someone else!

---

