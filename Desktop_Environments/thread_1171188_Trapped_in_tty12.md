---
title: "Trapped in tty12"
date: 2009-05-27
forum: Desktop Environments
---

### Post by Reech.out on 2009-05-27
Hi everyone,

I just changed my dualboot setup to Ubuntu only (running windows in Virtualbox).
In need this windows at regular basis to take over other Windows boxes using RAdmin.
This requires hitting ctrl+alt+F12 to send a ctrl+alt+del signal to the remote machine.
Witch, of course switches my to TTY 12 in Ubuntu.
The problem is that I cant seem to escape TTY 12 once I'm there.
I get a blinking cursor (no login) and none of the ctrl+alt+F(n) combos get me another TTY (cli or X) forcing me to reboot (or use ctrl+PrtScr+REISUB).

Is there any way of changing this behaviour so that ctrl+alt+F12 doesn't send me to TTY 12.

PS:I tried changing the RAdmin options to another key combination, but that's no use since I hit ctrl+alt+F12 more than half the time purely out of habit. #-o

Any input would be greatly appreciated.

---

### Post by Reech.out on 2009-06-01
Anyone?

---

### Post by zerocc on 2010-01-04
you may have to create a file: */etc/init/tty12.conf* which follows the format of the other tty.conf files, but changes the switches - you'll have to do that research yourself though!

---

### Post by Jenkins1 on 2010-01-04
I may be missing something but normal ctrl+alt+f7 gets you back to the graphical interface.

---

### Post by zerocc on 2010-01-04
> **zerocc said:**
> you may have to create a file: */etc/init/tty12.conf* which follows the format of the other tty.conf files, but changes the switches - you'll have to do that research yourself though!

oh, here you go:

*man 5 init*

---

