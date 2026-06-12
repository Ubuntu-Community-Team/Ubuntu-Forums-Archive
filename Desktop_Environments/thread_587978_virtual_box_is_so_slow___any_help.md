---
title: "virtual box is so slow   any help ?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by tropcky on 2007-10-23
hi i am using virtual box to run win xp on it     nad the problem is that its so slow   really slow 

is any help plez 2 fix that and make a bit faster  

 my pc is a old . its :
 processor  :2.5 cach 265 
 ram : 512 
  viga : ati 128 
  so ?????

---

### Post by tropcky on 2007-10-23
any help ???????

---

### Post by gaussian on 2007-10-23
> **tropcky said:**
> hi i am using virtual box to run win xp on it     nad the problem is that its so slow   really slow 

is any help plez 2 fix that and make a bit faster  

 my pc is a old . its :
 processor  :2.5 cach 265 
 ram : 512 
  viga : ati 128 
  so ?????

I tried running VirtualBox and QEMU+KQEMU with similar amount of RAM. It works fine if the guest OS is something like DSL (Damn Small Linux) that does not need much memory. But running XP on top of Ubuntu with that little memory was hopeless due to constant swapping. So basically my message is that you need more memory.

You could marginally improve things by making sure that you are not running any daemons/programs you don't need and that you are using something lite weight (like XFCE or IceWM) as windows manager. But I don't think it will help much.

---

