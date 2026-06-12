---
title: "Desktop disappears and goes to terminal"
date: 2013-08-27
forum: Desktop Environments
---

### Post by ronc68 on 2013-08-27
I have two computers and both experienced this.  One is Ubuntu 12.04 running gnome and the other is Xubuntu Xfce 12.04.  Both have done this and I have resorted to rebuilding the machines.  My daughter just called and her Xfce just did it again.  Each instance has occurred coming out of power saving mode initiated suspend.  The display seems to indicate we were in some kind of "Safe Mode" terminal.  I can logon but this does not return us to the standard desktop appropriate for the version we are running.  She is not technical and I'm not much better.  Help would be really appreciated.

---

### Post by ronc68 on 2013-08-27
Just got a call from my daughter - she left her Xfce machine in the terminal mode - it apparently when back to Suspend mode due to a lack of activity.  She tapped the keyboard and the normal desktop came back and she is back in business - strange but it appears to be a bug of some sort in the Suspend component.

---

### Post by papibe on 2013-08-27
Hi ronc68.

While in text mode try pressing either Ctrl+Alt+F7 or Ctrl+Alt+F8 to go back to the graphics mode.

You can go back to the text mode by pressing Ctrl+Alt+F1. There you can login and restart the machine if needed by running (to avoid a hard poweroff):
```
sudo reboot
```

Let us know how it goes.
Regards.

---

### Post by ronc68 on 2013-08-27
Thanks - the next time it happens I will test it.  Thanks again.

---

### Post by tgalati4 on 2013-08-27
There are times when the xorg server crashes or doesn't initialize properly and it dumps you to a terminal.  It's rare, but it does happen.  You can try *startx* and see what happens or as papibe suggests the control key sequence.  If it happens consistently when coming out of suspend, then there are some fixes you can apply to make the resume process more robust.  Basically look for the resume script and read the documentation contained within and experiment with uncommenting some switches.  It's trial and error.

So, does suspend and resume work on both computers?  Is this a consistent problem or once every few weeks?

This type of problem normally doesn't require a reinstall.  Just some tweaks to the resume scripts.

---

