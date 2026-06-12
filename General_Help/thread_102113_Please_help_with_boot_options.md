---
title: "Please help with boot options"
date: 2005-12-11
forum: General Help
---

### Post by JimMartin on 2005-12-11
Hello All:

My machine is set up with Ubuntu on one partition and Windows XP on another. Prior to installing Ubuntu, I had several options on how I could boot XP. Since installing Ubunutu, I only have one XP boot option.  How do I get those other options back? I have tried to edit the boot menu but I have NO idea what I'm doing and don't want to screw things up. 

I need to access those other options because, as usual, my Windows system is freezing up and I need to repair it.

Thanks in advance,

Jim

---

### Post by soulestream on 2005-12-11
hmm, interesting question.

You can use ntloader(xp) to boot ubuntu, that would give you back your options. (dont like that option)

Lilo will boot to ntloader, so you can boot multiple windows OS's from it, but I dont know how you can make grub do that. 

ie.   linux boot loader (select windows) --> then you get the windows bootloader --> then you pick what windows boot you want.


soule

---

