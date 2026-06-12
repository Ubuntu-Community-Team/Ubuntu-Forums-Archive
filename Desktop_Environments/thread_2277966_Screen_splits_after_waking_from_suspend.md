---
title: "Screen splits after waking from suspend"
date: 2015-05-12
forum: Desktop Environments
---

### Post by PenguinLust on 2015-05-12
Whenever I wake up from suspend, my screen splits. It's squished vertically, then a partial duplicate fills in below it. The mouse pointer then doesn't know what to do. This problem will persist after I log out. It's as if the system thinks the resolution is lower than it is, and makes bad assumptions on that.
I have an old Xnote LM40a. Lspci reveals:
> 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280/M9+ [Mobility Radeon 9200 AGP] (rev 01)
There are no additional drivers. LUbuntu 14.04.2 LTS and I think the Gnome desktop or Unity or something.

---

### Post by Vladlenin5000 on 2015-05-14
*If* there were proprietary drivers you could try that... Unfortunately for you there's currently no support from AMD to legacy hardware. Whatever you're getting now with the open source driver is what you'll ever get.

---

### Post by mörgæs on 2015-05-15
It's an old graphics cards and I'm not surprised that some strange stuff happens when running a heavy desktop environment like Gnome / Unity.

How does it behave in LXDE?

---

