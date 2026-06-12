---
title: "Wubi 32 on vista 64?"
date: 2008-12-28
forum: General Help
---

### Post by Fzang on 2008-12-28
^Will this work out alright? 

Also, what are the cons of something as simple and easy as wubi (because everything has cons!)? I've heard it was decreased harddisk read/writes but does that even matter if I'm just fidling around with the system?

And lastly, I already have vista 64 and ubuntu 32 installed, unfortunatly my ubuntu 32 is crippled because I tried resizing with GPartEd and is unbootable, however, I still use GRUB so would I need to
-remove native GRUB
-reinstall vista bootloader
-install WUBI and WUBI-GRUB

That's all, thanks

---

### Post by Jammanuser on 2008-12-28
> **Fzang said:**
> [COLOR="Red"]^Will this work out alright? [/COLOR]

Also, what are the cons of something as simple and easy as wubi (because everything has cons!)? I've heard it was decreased harddisk read/writes but does that even matter if I'm just fidling around with the system?

And lastly, I already have vista 64 and ubuntu 32 installed, unfortunatly my ubuntu 32 is crippled because I tried resizing with GPartEd and is unbootable, however, I still use GRUB so would I need to
-remove native GRUB
-reinstall vista bootloader
-install WUBI and WUBI-GRUB

That's all, thanks

Yes it should...though I don't know why you want 32-bit rather than 64-bit, though. ;) As for the cons of Wubi...unable to hibernate in Wubi, unlike in a real install, slightly slower performance, possibility of getting a "crc error" at bootup (like me), which will result in having to reinstall Wubi! :P

BTW, how did you screw up your Ubuntu real installation by simply resizing the partition with Gparted? Next time, I would suggest backing up all your data (including boot files) first, before attempting the process! :lolflag:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by Fzang on 2008-12-28
I guess WUBI's totally not for me then? I'm using a laptop and currently on native linux I use the hibernate since suspend doesn't work

I use hibernate instead of shutdown because a normal ubuntu boot from a fresh install takes way longer to start up than vista... odly enough

---

### Post by Jammanuser on 2008-12-28
> **Fzang said:**
> I guess WUBI's totally not for me then? I'm using a laptop and currently on native linux I use the hibernate since suspend doesn't work

Wubi works just fine for a test run of Ubuntu 8.10...however if you want it for long-term use, you will most likely want to install it to a real partition.

However, it is possible though to simply transfer your Wubi install to a dedicated partition with [LVPM]("http://lubi.sourceforge.net/lvpm.html"), which is what I did, and it worked just fine...;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by LRTIMKEN on 2008-12-30
You wrote's nice and I support you![NSK](http://www.nskcn.com/product/ShowClass.asp?ClassID=28) [nsk](http://www.nskcn.com/product/ShowClass.asp?ClassID=28) [NSK](http://www.9skf.cn/product/ShowClass.asp?ClassID=28) [nsk](http://www.9skf.cn/product/ShowClass.asp?ClassID=28)

---

