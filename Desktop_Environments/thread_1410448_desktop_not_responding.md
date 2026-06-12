---
title: "desktop not responding"
date: 2010-02-18
forum: Desktop Environments
---

### Post by f-bomb on 2010-02-18
Have had karmic 9.10 installed since October and am fully up to date.  Started noticing today what I thought was apps being slow, but it has degraded into the desktop not responding an a strange way for long periods of time.  The mouse still moves, but nothing responds to any click or hovers.  I can still navigate in the current focused windows via the keyboard, but nothing else.  A few keyboard shorcuts work, and I can Ctl-Alt-Del to restart, but that's about it.  I'm even in Failsafe Gnome and still get the same behavior after each restart.  CPU is pretty much idle as well, so there isn't some rouge proc hogging anything.  I'm installing Kubuntu now just to see if this is a Gnome specific problem.....

any ideas?

UPDATE - tried kde/kubuntu with pretty much the same results.  no hardware errors in the logs either....

---

### Post by f-bomb on 2010-02-19
bueller?

---

### Post by MooPi on 2010-02-19
Sound very much like a hardware issue surfacing. Boot to your Live CD and check memory. If nothing shows up continue the boot process with the live CD and from terminal ```
e2fsck -n /dev/sd**
```With the appropriate indication for your hard drive /sda1, sdb1 etc....
If errors are found run this command ```
e2fsck -p /dev/sd**
```This is checking your file system and correcting.

---

### Post by f-bomb on 2010-02-19
must have been a problem with my wireless mouse/keyboard combo.  Out of curiosity i switched to a regular mouse and keyboard and am not having any issues....weird.

---

### Post by Letrazzrot on 2010-02-19
I wonder if this is a USB related issue.

The reason I wonder is because I had what sounds like the same situation happen to me, as well.  In my case, I had plugged my wired USB mouse into a different USB port.  The mouse worked, but the desktop (or parts of it) stopped responding, much as you describe.  After restarting didn't fix the issue, I changed the plug on a hunch and everything started working again.

---

