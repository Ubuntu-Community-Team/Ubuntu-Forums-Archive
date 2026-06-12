---
title: "screen problems"
date: 2006-05-16
forum: Desktop Environments
---

### Post by jturnbul on 2006-05-16
Fresh install of Kubuntu on a new P4 with a Nvidia GeForce 6600 GT pci-e graphics card.  For some reason, once I start to open up windows and menus, etc, its starts to make black spots, in place of the windows or menus.  The black spots have various strands of colours throught out, and seem to accumulate as i continue to open more things, but seldom go away.  I tried taking some screen shots, but they do not take an acurate picture of the problem.  

Hopefully I am adequetly describing the problem, and some one is familiar with it.

---

### Post by Sutekh on 2006-05-16
I know *exactly* what you mean.  

The problem for me (and my 6600GT) was the open source **nv** drivers.  To fix this problem, I installed the non-free drivers using this thread

[Ubuntu Forums - HOWTO Latest NVIDIA Drivers](http://ubuntuforums.org/showthread.php?t=75074)

 - Method 1 is dead easy and will install the NVIDIA drivers from the Ubuntu repositories (v7667)

 - Method 2 is slightly more involved and will install the latest (or any) NVIDIA drivers from the NVIDIA website

Hope this works for you too.

---

### Post by jturnbul on 2006-05-16
thx bud, that did it.    Saved me from going back to FC

---

