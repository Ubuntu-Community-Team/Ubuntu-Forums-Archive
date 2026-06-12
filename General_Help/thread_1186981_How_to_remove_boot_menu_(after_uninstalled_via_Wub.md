---
title: "How to remove boot menu (after uninstalled via Wubi) on a dual boot Vista-Ubuntu PC"
date: 2009-06-14
forum: General Help
---

### Post by netlaptop on 2009-06-14
First, I have a laptop with Window Vista 64 bits installed. I have installed Ubuntu inside window via Wubi for testing new OS. 

It is OK so far with Ubuntu on my laptop, so I **uninstalled Ubuntu inside Window**, and **installed full Ubuntu** on new partition, and set it as a default OS for booting.

There is a small inconvenient that I have to choose 2 times if I wanna boot to Vista. There are 2 boot menus!!

 1- Choose Ubuntu 9.04 (full installation) or Window Vista.

 If I choose Window Vista, another boot menu appears:

 2 Choose Ubuntu (inside window) or Window Vista. 

I do not know why this 2nd boot menu is still there, even I have uninstalled Ubuntu inside.

Is there any way that I can remove the boot menu (I guess it comes from Ubuntu inside window version?)

I would like to boot directly to Window if I choose Window to boot at the 1st boot menu.

---

### Post by dandnsmith on 2009-06-14
You need to edit the file which gives the Windows menu, as this is where the wubi entry is.
It used to be boot.ini in what Windows considers to be the boot disk.
XP has a system method for editing it, but I don't know the equivalent for Vista.

---

### Post by netlaptop on 2009-06-14
Thanks. It is solved.
In Window Xp, We can easily config it with a file called "boot.ini", but in Window Vista it is different. Vista uses Window Boot Manager.
To edit it, we have to run "bcdedit" and type some command. There is a easy way to make changes to boot config data is using **EasyBCD **(EasyBCD is NeoSmart Technologies 100% free Vista bootloader modification tool).

Hope it helps saving time for others.

---

### Post by dandnsmith on 2009-06-14
That's something for my file of useful bits of knowledge.

---

