---
title: "mousecursor unusable after update today"
date: 2012-05-11
forum: Desktop Environments
---

### Post by jringoot on 2012-05-11
Running ubuntu 12.04
Since an update today, the mousecursor is unusable.
I tried gdm, lightdm, xfce4. 
All the same issue, even after a apt-get remove --purge of gnome, unity, xfce4, xorg, etc...n so that no GUI starts up and a reinstall of xfce4.

The issue is always the same, from the GUI login screen, and after login in the desktop environment.  The mouse cursor is only moveable in a band thinner than an inch wide on the left side of the screen, a right mouse click, pops up a menu on the far right side of the screen.
I also tried removing and reinstalling the synaptics driver, but no luck.

In windows 7 there is no such problem on this machine.

This is a dell E6420 latitude.

The machine is unusable in ubuntu GUI like this.

Thanks for looking into this.

---

### Post by jringoot on 2012-05-14
Got it resolved/worked around.

I had manually installed the nvidia driver from the website of nvidia, in the beginning, because I had problems setting up a secondary monitor.

Apparently I had apart from that graphics driver, as well the 
nvidia-current and xserver-xorg-video-nouveau installed.

I removed them all.
And just installed  the xserver-xorg-video-nouveau.

Problem solved.

I just need to test the secondary screen again.

---

### Post by jringoot on 2012-05-14
> **jringoot said:**
> Got it resolved/worked around.

I had manually installed the nvidia driver from the website of nvidia, in the beginning, because I had problems setting up a secondary monitor.

Apparently I had apart from that graphics driver, as well the 
nvidia-current and xserver-xorg-video-nouveau installed.

I removed them all.
And just installed  the xserver-xorg-video-nouveau.

Problem solved.

I just need to test the secondary screen again.
removed the xserver-xorg-video-nouveau and installed the nvidia-current.
Because: full resolution was not supported on external screen (1280x1024), only 600x800 worked.
With nvidia-current no such problem, both screens work with their maximum resolution.

---

### Post by jringoot on 2012-05-15
the problem is between the docking with external screen and laptop.
I end up with installing nvidia-current via apt for the dual display to work properly.
But then booting in laptop standalone gives me the unusable mousecursor, so I do "apt-get remove nvidia-current" And when I am back in the office I must reinstall it or I don't have the full resolution...

sigh

---

### Post by jringoot on 2012-05-15
To test, I installed fedora 17 in dual boot, tested, standalone, and with dual screen.

Apparently it is the xorg-x11-drv-nouveau driver version 0.0.16 release 34.20110720gitb806e3f.fc17

Tried a couple times with and without docking, there is no such issue with the mousecursor, no need to reconfig.

---

