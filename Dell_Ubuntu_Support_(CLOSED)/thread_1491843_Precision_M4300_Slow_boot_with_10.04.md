---
title: "Precision M4300 Slow boot with 10.04"
date: 2010-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tobbe1027 on 2010-05-24
Hi, with 9.10 my Dell booted in about 35 seconds and after 45 I was logged in. After a upgrade to 10.04 it takes more than two minutes and sometime more than tree to boot and logg in.

Anyone have any tips or solution

/Tobbe

---

### Post by dentaro16 on 2010-06-18
if there is any abnormalities with it taking too long to boot i would first find out if there is a hardware problem. better safe than sorry. run this to see if your hard drive is bad

[http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)

scroll down to Drive Fitness Test. fantastic tool

then try

memtest86 to check memory

if those pass and everything is good, boot into Ubuntu and run fsck. you could also make the computer just do it when you reboot.

open a terminal and type

```
shutdown -r -F now
```

see if those help at all

---

