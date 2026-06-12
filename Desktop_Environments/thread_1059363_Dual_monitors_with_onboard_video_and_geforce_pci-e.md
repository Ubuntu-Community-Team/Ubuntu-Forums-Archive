---
title: "Dual monitors with onboard video and geforce pci-e"
date: 2009-02-03
forum: Desktop Environments
---

### Post by jefco on 2009-02-03
I've just installed kubuntu 8.10 and am struggling to run two monitors with the existing onboard video (via S3 chrome) and a geforce 7600GS pci-e card. I've read many forum posts and done the following:

1. Set the bios to keep the onboard chip enabled in the presence of an external card.
2. Installed the restricted nvidia accelerated graphics driver (ver.177)
3. Ran 'X -configure' at the command line and copied xorg.conf.new to /etc/X11/xorg.conf.
4. Checked in xorg.conf that the openchrome driver was installed and confirmed it at the command line.
5. rebooted

The machine boots up initially with monitor1 (onboard video), then switches to monitor0 (geforce) for the GUI login screen. Monitor1 goes blank at this point while the desktop loads on monitor0. I can drag the mouse cursor into mon1, but it changes from the gui arrow to a white-outlined, low res X. It switches back to the arrow when it's back on the desktop on mon0, but I can't drag any graphical elements into mon1, they just stop at the edge of of the screen. Occasionally I'll move the cursor to mon1 and it will remain as a GUI arrow, but then the desktop freezes (no response to mouse or keyboard, including alt-Fx when I try to bring up a new tty screen) and I have to hit the reset button.

I'm a noob & know nothing about the X-window system, but is it possible that mon1 is being managed by a different window manager than mon0? If so, what to do?

System is a core2 duo E6600 with 2gb ram and the P4M900/890 chipset.

thanks...

---

