---
title: "Reducing Boot time - shorten LILO bios check?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by MikeMLP on 2006-06-27
I'm currently dual booting XP and Ubuntu using the GAG LiveCD and have installed Lilo into my ubuntu partition, thus retaining my MBR and NTLDR  I've noticed that every time I start up, Lilo checks the bios.  Displayed during that time is something kind of like this 

Lilo boot manager v. **.**.** Loading Linux Kernel....................................................
Bios Check Complete

and then it continues.  The bios check takes about 2-3 minutes though, and I'm wondering if this is really necessary every time I start up.  If it is, then is there any way to make the wait time shorter?

Thanks!

---

### Post by barbedsaber on 2008-06-02
I know this is a zombie thread, but I am having the same problem, in hardy.
anyone?

---

### Post by MikeMLP on 2008-06-02
You are using LILO and not GRUB, right?  And if so... Why?  I'm curious, because the only reason why I did LILO on the install partition + the GAG livecd was because I was trying to be extra careful with my MBR.  I was paranoid about touching it because I was just trying out linux for the first time.  I was not yet confident in the associated software.  

Since then, I've always just used GRUB and installed it on the MBR.  I would think that GRUB on the linux install partition would work as well, and probably go much faster than LILO - check websites and documentation before doing this though.  I never was able to figure out how to make LILO go faster.

As far as I know, there is no reason to use LILO now though - I've let GRUB write over my MBR many times without issue.

-Mike

---

