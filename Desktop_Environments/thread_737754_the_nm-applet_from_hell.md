---
title: "the nm-applet from hell"
date: 2008-03-27
forum: Desktop Environments
---

### Post by BetterSense on 2008-03-27
Somehow, I started getting two instances of nm-applet, in Gnome, in the taskbar instead of the usually sufficient 1. So i have two wireless network signal bars right next to each other and it's stupid. Nobody needs two identical network managers running.

So I went into the console and killed one of them. But it returned upon relogging in. 

So I went into the console and killed them both, and it returned upon logging in. 

So I went into Administration->Sessions and unchecked the 'remember running application' box, and it STILL returned upon relogging in.

So I unchecked it from the list of startup apps, made sure I unchecked the 'remember running applications', killed them both using killall, and BOTH OF THEM still returned upon logging in. 

Somebody please help me. I need help!!

---

### Post by Islington on 2008-03-27
so just to be clear did you right-click..remove from panel?

---

### Post by fracturedmorals on 2008-03-27
> **Islington said:**
> so just to be clear did you right-click..remove from panel?

nm-applet is actually a tray application. No point in trying that one....

---

### Post by Islington on 2008-03-27
> **fracturedmorals said:**
> nm-applet is actually a tray application. No point in trying that one....

Oh darn you are right, not thinking there...

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/47825](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/47825)

possibly related?

[http://ubuntuforums.org/showthread.php?t=191708](http://ubuntuforums.org/showthread.php?t=191708)
check out post #10

---

