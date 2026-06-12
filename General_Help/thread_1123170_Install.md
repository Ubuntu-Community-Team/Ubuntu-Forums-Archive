---
title: "Install"
date: 2009-04-11
forum: General Help
---

### Post by brampt1 on 2009-04-11
Hi,
I'm going to remove Vista from dual boot. How should I partition my hard drive when I reinstall Ubuntu?  It's 500gbs.
Thanks

---

### Post by defaultusername on 2009-04-11
brampt1,

Partition according to your tastes. How are you planning to use Ubuntu? A typical desktop installation does fine with the default partitioning scheme.

---

### Post by taurus on 2009-04-11
Create three partitions:  /, swap, & /home.  The reason you want a separate /home so that you can keep all your personal files and settings if you have to reinstall or upgrade later.

20GB for / should be plenty.  Make swap either about the size of your RAM or double it.  Then, leave the rest for /home since that is where you will store all your downloads unless you want to make / larger.

---

### Post by brampt1 on 2009-04-11
Thanks,
I thought I should separate my home files. I will have options during installation right?

---

### Post by taurus on 2009-04-11
You can use gparted from the LiveCD (System -> Administration -> Partition Editor) and partition your harddrive first.  Then when you get to Step 4 of 7 during the installing process, pick Manual option and tell the installer to _mount_ whichever partition to / and the other one to /home.  And if the swap is not mounted (no keys in front of it), then mount it to swap.

---

### Post by brampt1 on 2009-04-11
Thanks  :)

---

