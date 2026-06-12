---
title: "Windows programs on Ubuntu"
date: 2005-11-13
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-11-13
Hey.

I'm quite new to all the Linux buis, but very exited.

There are, however, some programs I didn't find a proper replacement for, and I'd like, for the time being, use my WIN programs.

I understood there is WINE to install windows programs on. But nor did I manage to install the programs I need n wine, neither on Crossover Office.

Ay other possibilities?

Thanx

Gabriel

---

### Post by ssam on 2005-11-13
what programs do you need to replace?

---

### Post by aysiu on 2005-11-13
If you name the programs, people will be able to tell you want the most appropriate venue is:

1. Wine
2. Crossover
3. Linux alternative
4. Dual-boot

---

### Post by GabrielWolff on 2005-11-13
[QUOTE=ssam]what programs do you need to replace?[/QUOTE]

Finale, a notation program. I'm trying to find something linuxish, but I really have to continue writing music for the time being, and a program that shecks out ATRAC3 to a NetMD. 

Is there any other platform like wine?

Gabriel

---

### Post by junior aspirin on 2005-11-13
ur gonna have to dual boot for your net-md. i have one, and sony sucks big time . nothing on linux, and crappy software on windows. cant wait till i get my iriver for christmas :p

---

### Post by GabrielWolff on 2005-11-13
[QUOTE=aysiu]If you name the programs, people will be able to tell you want the most appropriate venue is:

1. Wine
2. Crossover
3. Linux alternative
4. Dual-boot[/QUOTE]

Are 3 and 4 programs like the first second?

Gabriel

---

### Post by GabrielWolff on 2005-11-13
[QUOTE=junior aspirin]ur gonna have to dual boot for your net-md. i have one, and sony sucks big time . nothing on linux, and crappy software on windows. cant wait till i get my iriver for christmas :p[/QUOTE]

How do I do that? Does it mean to install XP once again? How?

Gabriel

---

### Post by bluemuffin on 2005-11-17
Hello!

I found it easier to install ubuntu in an existing XP machine. Like reinstall XP and then installing ubuntu. Follow instructions until the partitioning then choose manual partition. 

The #1 choice (hda1 with the NTFS) is your windows directory or folder, don't touch it. 

Configure #2 choice instead (Ext3 or reiserFS, mount as /, erase existing directory, etc.)

COntinue with the partinioning and installation.

That's it, it worked fine with me. I can dual boot now since the Grub loader gives me a choice between ubuntu and xp.

It might work the otehr way (Linux first, then XP) but I did not try it because my very short experience with linux taught me that windows is uncompromising with it.

:smile:

---

### Post by Cyril on 2005-11-17
If you do not wish to reinstall xp you can always resize the partition to make space for ubuntu instead.

---

