---
title: "max performence"
date: 2010-09-22
forum: Desktop Environments
---

### Post by gudurukarthik on 2010-09-22
hi , im running ubuntu on a sony fw series 6 gb ram laptop. my question is , i think ubuntu is not using my total ram , and i got this after i had seen the system monitor and it shows   ''memory :2.9gb''. 
can any one help me in solving this problem . and please tell me if any thing else i should be doing to improve my laptop performance .
thank you

---

### Post by jfreak_ on 2010-09-22
I think you are using 32-bit ubuntu. 64-bit will make available all the RAM. There is a workaround for 32-bit kernels to use all the RAM but I am not sure how to do it. Google it.

---

### Post by gudurukarthik on 2010-09-22
hey thank you , and as im new to ubuntu can u please tell me where can i check whather im using 32 bit or 64

---

### Post by PRC09 on 2010-09-22
This will tell you if you are using 64bit.From a terminal type:

```
uname -m
```

There is a PAE kernel that will make all the ram available but 64bit would probably be better.There is no way that I know of to upgrade from 32bit to 64bit other than re-install with 64bit.See link attached for PAE info....


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by gudurukarthik on 2010-09-22
hey it replays i 686 ... so what's it mean

---

### Post by PRC09 on 2010-09-22
That means you are using 32bit.....

---

### Post by roggenschrotbrot on 2010-09-22
try
```
getconf -a | grep -i long

```
the value of LONG_BIT is what you want to know

---

### Post by gudurukarthik on 2010-09-22
it says :

LONG_BIT                           32
ULONG_MAX                          4294967295
 

so what sould i be doing 
thank you a lot for ur helping nature

---

### Post by PRC09 on 2010-09-22
The choice is yours,you can instal the PAE kernel which has the instructions in the link or you can download the 64bit Ubuntu disk and re-install .Personally I would try the PAE route and see if it makes a difference in your performance.I run both and dont really notice much difference but I dont do alot of work with cpu intensive things which is where the 64bit would be an advantage.....

---

### Post by roggenschrotbrot on 2010-09-22
if you want a notable improved performance you could also test a lighter desktop environment like xfce or a standalone window manager like openbox.

---

