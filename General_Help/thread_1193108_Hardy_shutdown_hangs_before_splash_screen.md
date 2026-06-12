---
title: "Hardy shutdown hangs before splash screen"
date: 2009-06-21
forum: General Help
---

### Post by VOLKOV9 on 2009-06-21
Problem: When I shutdown, either with the physical power button or the logout button applet, it closes all visible programs (including panels), and hangs, with me staring at the desktop picture.  I've found other posts with people in similar situations, who think it's being caused by a program that's refusing to shut off, but I can't get a terminal open while this is happening (even my keyboard shortcut won't bring one up at this point).
Note: After installing Cairo dock, Cairo dock doesn't close either, but its buttons are unresponsive.  Regardless, this problem existed before I installed Cairo dock.

Unsatisfying solution: When it is hanging thusly, I can press the physical power button again, and it then continues to shut down.  But this makes it shut down whether I wanted to shut down or reboot.  CtrlAltBkspc and ```
sudo init 0
``` both work, so basically the only practical problem is a lack of simple reboot.  But the thing should also just work properly.

Context: I recently reformatted/reinstalled Hardy.  everything was great, until a day later I noticed some kernel panics going on.  Recalling a similar situation when I had Hardy before (<http://ubuntuforums.org/showthread.php?t=1028679>), I ran ```
sudo apt-get --reinstall install linux-backports-modules-hardy
```.  Frighteningly, the kernel panics did not subside, and this started happening.  The next day, the kernel panics seem to have stopped, eerily...

PS: editing /etc/init.d/alsa-utils does nothing.

---

### Post by VOLKOV9 on 2009-06-23
Got a terminal window open: keytouchd was the culprit.

Solution: [http://ubuntuforums.org/showthread.php?t=853312&](http://ubuntuforums.org/showthread.php?t=853312&)

very minor detail: the solution does not apply till the next time the computer starts up, so change the file, kill keytouchd, and reboot.  tada.

---

### Post by VOLKOV9 on 2009-06-24
The fix above actually "solves" the problem by preventing keytouchd from loading @ startup.  Not ideal.  So ignore that and use the following: [http://sidux.com/PNphpBB2-viewtopic-t-11289.html](http://sidux.com/PNphpBB2-viewtopic-t-11289.html) (scroll down to the 7/3/08 post by houms).  Perfect.

---

