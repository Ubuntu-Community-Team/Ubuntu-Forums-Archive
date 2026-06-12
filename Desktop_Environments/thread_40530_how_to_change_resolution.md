---
title: "how to change resolution?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by irado on 2005-06-09
:???: 

HI, nice people

I am unable to change the resolution in my Ubuntu. It simply accept ANY configuration, and opens with 600x800, even when asking it for another higher one (1240x800).

The driver is appropriate for the video and monitor (Intel - i810 driver), but I am stuck  ](*,) 

any suggestion? 

TIA

---

### Post by bored2k on 2005-06-09
Upper panel - applications - system tools - terminal
Here type
> sudo dpkg-reconfigure xserver-xfree86 or > sudo dpkg-reconfigure xserver-xorgIf you are on Hoary.

Then,  Input your password then follow the steps. After you are done, reboot your computer.

---

