---
title: "Hard Drive size !!!!!"
date: 2011-03-29
forum: Desktop Environments
---

### Post by elliotbeken on 2011-03-29
Hi all, 
       i have kubuntu 10.10 64-bit and all works fine on my compaq cq-61 apart from one thing. if i highlight the folders in root and right click properties it starts to count the folders/files and calculates the space i have used/left.  All goes well till a few seconds in and it jumps from 30gb to 128Tib!!!!!..... what does this mean i have attached a screen shot.

thanks

---

### Post by dabl on 2011-03-29
I can only think of two possibilities:

1. A bug in Dolphin (but it works correctly for me on 3 systems)

2. Corruption in your filesystem.

You could boot a Live CD or USB stick, and run fsck from there, to make sure the filesystem is OK.

Also, if you open a terminal and run df or du does it present the sizes correctly?

---

### Post by elliotbeken on 2011-03-29
yeh now you have said it might be a dolphin bug i am starting to think the same as the terminal commands show the correct size 

thanks

---

### Post by kio_http on 2011-04-01
Which version of KDE and dolphin are you using.

In dolphin,

> Menu
> Help
> About KDE
> About Dolphin

---

### Post by elliotbeken on 2011-04-01
Dolphin version 1.5

---

