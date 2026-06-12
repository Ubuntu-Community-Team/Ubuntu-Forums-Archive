---
title: "Hibernation mode not working. Just black screen?"
date: 2009-04-06
forum: General Help
---

### Post by villevalorox on 2009-04-06
Hello all! I need your help. My hibernation mode is not working. It used to but just stopped one day. I'm not for sure if it was something I installed or what. When i try to send my computer into hibernation mode I just get a black screen with the white typing thing blinking.  I'm in 8.10 and it used to work in it. Please help!! :) thanks XD

---

### Post by JC Cheloven on 2009-04-06
> **villevalorox said:**
> Hello all! I need your help. My hibernation mode is not working. It used to but just stopped one day. I'm not for sure if it was something I installed or what. When i try to send my computer into hibernation mode I just get a black screen with the white typing thing blinking.  I'm in 8.10 and it used to work in it. Please help!! :) thanks XD

Do you have a big enough swap partition? At least the size of your ram is needed to hibernate.
And, is it enabled?

--> You can check it out with the "top" or the "free" command at a terminal. If you need more help, please give us the output of
```
free
```
and
```
sudo fdisk -l
```

---

### Post by villevalorox on 2009-04-06
Yes to the first and how do I see if it is enabled?

---

### Post by JC Cheloven on 2009-04-06
> **villevalorox said:**
> Yes to the first and how do I see if it is enabled?

For example in the free command: a number different from zero should appear on teh side of "swap:". Here is my output, for example:

> jc@carillon:~$ free
             total       used       free     shared    buffers     cached
Mem:       3111600     879148    2232452          0      63168     425352
-/+ buffers/cache:     390628    2720972
Swap:      4707004          0    4707004

---

### Post by villevalorox on 2009-04-06
K this is what I got ... lol I have no clue what it means :(

But It did work.. I do not get why it would just stop working. :(




> david-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2063144     883276    1179868          0      20624     235984
-/+ buffers/cache:     626668    1436476
Swap:      1397612          0    1397612


---

### Post by JC Cheloven on 2009-04-07
Oh... it means that you have about 2Gb RAM, and only 1.3Gb of swap space. 

The expected behaviour in this situation is that hibernation wont work at all. I'm unsure about the reason it works for you sometimes. I guess it depends on whether the amount of ram the system is using when you try to hibernate is small enough.

Anyway, you should setup a swap space larger than 2Gb. It will involve to boot from live cd, start gparted, shrink a partition which is side-to-side whith your swap, and to make bigger the swap partition accordingly. Try ending up with about 3Gb of swap.

It may take a while, but the previous procedure allows you to leave unchanged your configuration files (fstab ...).
EDIT: or maybe not, and you have to do a litle editing ; anyway do that I told and let us know.

---

