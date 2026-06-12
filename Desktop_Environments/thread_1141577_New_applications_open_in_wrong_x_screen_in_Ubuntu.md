---
title: "New applications open in wrong x screen in Ubuntu"
date: 2009-04-28
forum: Desktop Environments
---

### Post by caseyb on 2009-04-28
I have a dual monitor setup (NVIDIA) and each has its own x screen in Ubuntu 9.04. Everything works as it should in screen 0. When I open an application in screen 1 (using any menu, e.g., Applications, Places, etc., if I click on the trash or on the volume), it opens in screen 0 instead of screen 1. For some odd reason, Firefox opens correctly.

  So to get an application to open in screen 1, I hit Alt-F2 and type the program name. This always works but is thoroughly annoying and rather inefficient. How can I make it so that new apps automatically load in the screen I am working in? Is there something incorrect with my configuration?

An additional issue is that when I configure my workspace pager on screen 1 for 4 columns, it still only displays 2.  I cannot add more. It's as if screen 1 is not being able to write its own configuration, although modifications I make to the toolbar in screen 1 remain.

Thanks for your help.

(The release notes for 9.04 said somewhere that there was better dual monitor support, so I was hoping upgrading would have resolved this issue but it hasn't.)

---

### Post by cwmusson on 2009-04-28
I have the same issue.

e.g. galeon, gnome-terminal, gnome volume control, etc opened from gnome panel always opens in screen 0, even if panel is in screen 1 or 2.  Alt=F2 launch works fine.

firefox and prism don't seem to be affected.

---

### Post by cwmusson on 2009-04-28
The official bug report appears to be here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/339783)

There is a workaround (use 'bash -c') mentioned in the bug report.

---

