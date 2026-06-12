---
title: "how to correct a segfault error?"
date: 2009-04-30
forum: General Help
---

### Post by gfunkera on 2009-04-30
ive been trying to get a CD to burn in brasero.. i know its possible because ive done it before.. the brasero software crashes after its opened ... the crash occurs at a seemingly pre determined amount of time after brasero is opened.. so it doesnt matter if the actual burning process has begun or not..

it seems to be an error (error code 4) in two of the libraries on the machine.. "libgstriff....." and "libglib...."

i did a dmesg right after the crash and this is the last two lines of the dmesg:
[B]
[  580.683276] brasero[3847]: segfault at 1e0e7e11 ip b1e17668 sp b26c3060 error 4 in libgstriff-0.10.so.0.16.0[b1e11000+b000]
[  665.366853] brasero[3853]: segfault at ffffffff ip b7376bcb sp b4e65a00 error 4 in libglib-2.0.so.0.2000.1[b731e000+b6000][/B]

thats as much as i know, any ideas on how to fix?

---

