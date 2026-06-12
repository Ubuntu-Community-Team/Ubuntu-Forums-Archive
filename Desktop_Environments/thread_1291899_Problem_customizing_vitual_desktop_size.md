---
title: "Problem customizing vitual desktop size"
date: 2009-10-15
forum: Desktop Environments
---

### Post by pepitofernando on 2009-10-15
Hi forum users.

 Here is the problem I have.

I've got a Hannspree netbook, 10" screen, with intel 945 Grafics card (driver intel for Xorg).

  The problem is that in the auto-scaning for the screen modes, it only sets the "standar" not virtual modes, so when I try to set the screen to virtual sizes with the Gnome aplication, i can't. So I used the xrand utility with the efects you can see in the attached image. The desktop resizes, but Gnome dont seem to notice, and the panel remains in the non-virtual position, the windows dont get maximized covering all the aviable space. I've tried to add a subsection "device" in the Xorg.conf, with no efect. The only way i found to make a "virtual size" is to put the xrand comand in the startup applications, with the undesired effect commented (not practical at all).

Any ideas of how to tell Gnome to use virtual sizes in its configuration tool for the resolution?

Thank you very much

(my english may not be very good, sorry for it, not from english speakig country)

---

