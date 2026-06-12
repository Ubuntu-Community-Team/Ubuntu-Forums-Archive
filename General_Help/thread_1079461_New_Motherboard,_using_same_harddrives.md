---
title: "New Motherboard, using same harddrives?"
date: 2009-02-24
forum: General Help
---

### Post by silverwolf636 on 2009-02-24
I am getting a new mother board and am going to use the same hard drives that I am using now.  
I am jumping from a 1.7 to a 2G. Not much but is still may matter.
Do I have to redo my hard drives or will 8.04 Ubuntu 32bit identify the new system and reconfigure?
I am also upgrading the RAM from 1G to 2G. 
Will Hardy 32bit access the 2G?

Thanx

---

### Post by rbmorse on 2009-02-24
Unlike certain other operating systems, every time a Linux, like Ubuntu, loads it checks the hardware configuration and loads the appropriate drivers based upon what it finds at boot time. 

The user can modify this, of course, but in general you should not have any problems doing a motherboard switch, unless there is some specific hardware compatibility/support issue related to the new motherboard.  For example, if the new board has a LAN chip or disk controller that isn't recognized by the Linux kernel you could experience difficulties related to those subsystems.

---

### Post by mb_webguy on 2009-02-24
> **silverwolf636 said:**
> Will Hardy 32bit access the 2G?

With 32-bit you can go up to 4GB of memory.  More than that, and you need a 64-bit OS (and, of course, a 64-bit processor).

---

### Post by silverwolf636 on 2009-02-25
Ok, great and thanks for the replies....

---

### Post by Slim Odds on 2009-02-25
> **mb_webguy said:**
> With 32-bit you can go up to 4GB of memory.  More than that, and you need a 64-bit OS (and, of course, a 64-bit processor).

Almost 4G, a little less...

---

