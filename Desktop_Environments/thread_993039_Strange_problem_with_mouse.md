---
title: "Strange problem with mouse"
date: 2008-11-25
forum: Desktop Environments
---

### Post by r0y4l on 2008-11-25
Hello Guys,

after upgrading to Ubuntu 8.10 my mouse does not work correctly any more.

After some minutes/hours the mouse stops clicking, I can still move the mouse but I can not click any window, button, etc. only restart of the X server works for fixing this problem.

I tried several mouses, a hardware defect is not possible and also several usb interfaces.

I had this problem with KDE and Gnome. Sometimes everythign works fine for hours but then... I restarted X six times this day and that sucks!

Can anyone help me with this problem?

There is also no error in dmesg or Xorg.0.log...

---

### Post by Atolla on 2008-12-05
I have the same problem in Kubuntu 8.10. It seems to be related to heavy memory consumption, since it happens when I'm editing a large image file in GIMP. Restarting X (CTR+SHFT+BACKSPACE) deals with it.

Does anybody know how to solve this problem, it's really irritating!

EDIT: After clearing up 1GB from my home folder it took much longer before it happened. Before I had only 30mb of free disk space there. But still the problem keeps being there!

EDIT2:
Solved?

I have a dual monitor setup. I read some post here:
[http://www.linuxquestions.org/questions/linux-hardware-18/mouse-partially-stops-working-randomly...-676334/](http://www.linuxquestions.org/questions/linux-hardware-18/mouse-partially-stops-working-randomly...-676334/)

Which resolved the issue by ditching xinerama and switching to twinview in /etc/X11/xorg.conf

So far no problems!

---

