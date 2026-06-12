---
title: "Weird problem after upgrade 10.04 to 12.10"
date: 2012-11-23
forum: Desktop Environments
---

### Post by Yip on 2012-11-23
One month ago I installed xubuntu on my notebook, all was running fine until now.

I have a dual boot system with windows 7 as the primary O.S. Today I have upgraded xubuntu from 12.04 to 12.10, but after rebooting this is what I see:

grub4dos 0.4.5b 2011/11-27 MWM 628K/2485M/1408M, end: 35560D

[ Minimal bash-like editing is supported. For the first word, TAB completitions of a device/filename ]

grub> ...


I have tried typing "boot" and it says "unable to boot, load kernel first".

What should I do to fix this ?

---

### Post by Yip on 2012-11-23
Well... I have solved the problem... just had to install the latest version of EasyBCD and rewrite grub, sorry for this topic, I'll mark this as solved.

---

