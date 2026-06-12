---
title: "Important difference between Ubuntu 11.04 and CentOS 6 in desktop"
date: 2011-09-14
forum: Desktop Environments
---

### Post by Jettbot on 2011-09-14
I'm evaluating CentOS 6 vs Ubuntu 11.04 for my server + desktop needs by booting off of a thumbdrive on a box currently running Win 2008 R2.

When I boot into CentOS desktop, an error pops up immediately indicating that one of the SATA drives in a Windows software RAID has alot of errors and may fail soon. I suspected this to be true as I built a crappy test software RAID out of a bunch of spares I had lying around just to play with. So I'm really happy CentOS warns me right away. But when I boot into Ubuntu, I do not get any warning and if I go into disk util, it says that that specific drive has some errors but nothing serious.

Why the difference and how to I get Ubuntu to err on the side of safety like CentOS is doing?

CentOS 6 disk util is 2.30.1. 
Ubuntu 11.04 disk util is 2.32.1. 

Is it just a difference in versions or is there an error threshold setting or alarm setting I need to tweak?

Thanks!

---

