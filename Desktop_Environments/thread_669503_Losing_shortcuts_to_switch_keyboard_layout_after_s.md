---
title: "Losing shortcuts to switch keyboard layout after startup"
date: 2008-01-16
forum: Desktop Environments
---

### Post by warmrobot on 2008-01-16
Just after system has started I can't change keyboard layout.
And each time I have to click on System/Preferences/Keyboard
The checkbox "Layout Switching" by Alt+Shift is **checked** (!). But it does not work.
So I uncheck it, and check again. Now layout start to switch.
But after each start of system I have to do all these things again.

I have Hardy Heron alpha 3.
Why thats happening? What do you think? Thank you.

---

### Post by Angelos72 on 2008-05-06
Do you still have the problem in the final Hardy release?

I have installed the final release of Hardy and I have the same problem.

In fact my 

/etc/x11/xorg.conf 

says that the the only keyboard that I have installed is the US, but in the keyboard layouts application (I use gnome) I can see that the Greek keyboard is also installed.

What I have to do every time I reboot, is uninstall and then install the Greek keyboard. This solves the problem until next reboot.

If I reconfigure the xorg.conf file using:

```
sudo dpkg-reconfigure xserver-xorg
``` 

and set "gr" as the default keyboard then I cannon switch back to the "us" keyboard.



I would appreciate any help:confused:

---

### Post by Angelos72 on 2008-05-08
It seems this is a known bug.

Several work-arounds are proposed at the relevant launchpad site, where the bug is described as:

"[hardy] keyboard layout switching shortcut doesn't work after reboot"

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277")

---

