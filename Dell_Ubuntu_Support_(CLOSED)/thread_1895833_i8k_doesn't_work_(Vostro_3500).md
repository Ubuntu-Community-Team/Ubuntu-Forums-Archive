---
title: "i8k doesn't work (Vostro 3500)"
date: 2011-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sidowaty on 2011-12-15
Hi,

According to [https://wiki.archlinux.org/index.php/Dell_Vostro_3500#Fan_Control](https://wiki.archlinux.org/index.php/Dell_Vostro_3500#Fan_Control) i8k should work with my Vostro 3500. But I have strange problem with it (and also speedfan on windows, which also should work...). 
I've installed 1.33 i8kutils, loaded kernel module. Temperature is read ok, but I cannot set fan speed. I have all time:

```
# i8kfan 
-1 2
``` 

```
# i8kfan 2 2
-1 2
``` 

```
# i8kfan -1 1
-1 2
``` 

Here is dmesg:
```
[  859.320404] i8k: unable to get SMM BIOS version
[  859.326912] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)
```
(I see i8k warning but read that driver should work anyway)

My BIOS version is A04. Ubuntu 11.10, kernel 3.0.0-15 (but doesn't work also on 2.x). 

Have anyone this problem and fixed it?

Thanks,
Sid

---

