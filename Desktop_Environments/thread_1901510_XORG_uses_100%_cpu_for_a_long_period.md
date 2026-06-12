---
title: "XORG uses 100% cpu for a long period"
date: 2011-12-28
forum: Desktop Environments
---

### Post by BertN45 on 2011-12-28
The system is a P-IV 2,4gHz with 256Mb of memory. I use Lubuntu 11.10 and have xrdp installed. The system is constantly used by the children, but I wanted to change a few things so installed xrdp. 

XRDP works, but on the host system the P-IV the cpu runs at 100% for 10-30 seconds after I display a windows. The culprit is xorg, that takes between 70-80% of the cpu also after the window is displayed on the guest system. For the guest system I use the Remmina client. 

The cpu load has never been that high when I used xrdp in the past on Ubuntu/Gnome. Also a Windows XP system on a P-III 500mHz and 384MB works perfectly with the same client. The memory used by the host system was around 170MB leaving about 70MB free for cache etc.

The combination LXDE and xorg seem to create this high cpu load for this prolonged period of time. The cpu is not too slow and memory seems also enough.

Is the problem known by more persons and what can I do about it?

---

### Post by MichZem on 2012-06-05
I encounter a similar problem on ubunutu 12.04: 
once I open **Remminna** and try to connect to a remote ***windows OS***, my cpu raises to 100% , mostly because of the **Xorg** process ... 
In case you had a solution, I'll be happy to learn about it.

---

### Post by hakermania on 2012-09-12
Please confirm this bug if you are affected: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/997075](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/997075)

---

