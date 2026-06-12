---
title: "Mouse has gone crazy..."
date: 2008-10-28
forum: Desktop Environments
---

### Post by redgsturbo on 2008-10-28
Booted up my laptop this morning (default one day old intrepid build) and the mouse has started doing strange things... using the post thing embedded in the keyboard keeps jumping seemingly randomly... double click and hold to drag items stopped working... double click and hold to drag an open window by its titlebar still works.  double click to open a folder on the desktop doesn't work anymore... how do I fix this or at least reload the default configurations for X11 in its entirety?

---

### Post by lunarcloud on 2008-10-28
They updated, broke, and fixed xorg input drivers, just try updating.

Perhaps, reboot, go into the repair/recovery thingy in grub.

choose fix X.org or xfix or whatever.

---

### Post by redgsturbo on 2008-10-28
> **zarquad said:**
> They updated, broke, and fixed xorg input drivers, just try updating.

Perhaps, reboot, go into the repair/recovery thingy in grub.

choose fix X.org or xfix or whatever.

I am a gentoo guy... looking at the xorg.conf file, there was no screen setup or any thing other than loading the nvidia driver....  does ubuntu reference a different location for the xorg.conf?  how does x get configured?

---

### Post by redgsturbo on 2008-10-28
That seems to have worked... now though, if the mouse is moving at all and I click, the pointer jumps a great deal to the direction the mouse is moving, proportionate to how fast the mouse is moving... ??

---

### Post by jacekpod on 2008-10-29
i hope following link helps :idea:

[http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml]("http://www.idevelopment.info/data/Unix/Linux/LINUX_ErraticMouseBehaviorwithMouseFedoraandBelkinKVM.shtml")

---

