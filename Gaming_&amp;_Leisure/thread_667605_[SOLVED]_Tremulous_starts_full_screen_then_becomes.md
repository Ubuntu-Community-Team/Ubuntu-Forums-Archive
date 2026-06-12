---
title: "[SOLVED] Tremulous starts full screen then becomes windowed"
date: 2008-01-14
forum: Gaming &amp; Leisure
---

### Post by doug-M on 2008-01-14
I'm trying to play Tremulous but I have a problem.

It works fine for a while but after a few minutes of playing in full screen Tremulous jumps to a window and I cannot control the game or anything on the desktop.

The only way I have been able to get out of it is to ctrl-alt-F1 to a text console and kill Tremulous then ctrl-alt-F7 back to my X desktop.

I'm using nvidia restricted drivers on an nVidia Quatro NVS 135M video card on Ubuntu 7.10.

Any ideas on how to stop this from happening? Sometimes it seems to happen if something has popped up on the desktop, such as a new IM message.

Thanks

---

### Post by carlinuxlearner on 2008-02-09
I am having the exact same problem.

C@RL

let me know if you find a fix.

---

### Post by carlinuxlearner on 2008-02-09
Hey I found the fix! Here: [http://ohioloco.ubuntuforums.org/showthread.php?t=659754&page=2](http://ohioloco.ubuntuforums.org/showthread.php?t=659754&page=2)

As "gsiliceo" said "If you disable your screensaver, the problem goes."

I tried it and it worked!!

C@RL

---

### Post by doug-M on 2008-02-10
Yes turning off the screensaver seems to do it:

killall gnome-screensaver; tremulous

---

