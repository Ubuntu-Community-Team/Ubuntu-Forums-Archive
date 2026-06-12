---
title: "Adding a dual boot to Ubuntu"
date: 2005-11-14
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-11-14
Hey.

How do I add XP to a machine which has only Ubuntu running on it? 

I got the Install CD and all, I'm just not sure I won't be really sorry when realizing any Info on the machine is gone after installing XP. 

I wanna keep Ubuntu, but add XP.

Gabriel

---

### Post by Hellaxe on 2005-11-14
You should run GRUB again.
I think there's a how to here in the forum.
Make a search please.

Hope it works

---

### Post by aysiu on 2005-11-14
You'll have to:

1. Back up all your work.
2. I'm not kidding. Back up all your work.
3. You wouldn't ride a motorcycle without a helmet, would you (even if you had only a .01% chance of being in an accident)? Back up all of your files.
4. Resize your partition to make room for Windows. This can be done with a live CD (Ubuntu/ Knoppix) and a program on it like QTParted or gParted.
5. Install Windows
6. [Restore Grub to the MBR.](http://ubuntuforums.org/showthread.php?t=24113)

I can't emphasize enough how important #1-3 are. If you have to burn 150 CDs to back up your work or load up 800 floppies, do it. If your files are important to you, always back them up.

---

