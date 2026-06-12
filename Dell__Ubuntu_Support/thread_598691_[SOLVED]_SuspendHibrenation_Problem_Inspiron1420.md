---
title: "[SOLVED] Suspend/Hibrenation Problem Inspiron1420"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by unoodles on 2007-10-31
For users with intel Video cards type the command:

sudo apt-get install xserver-xorg-video-intel

Make sure your /etc/X11/xorg.conf uses the "intel" driver and not "i810"

Suspend/hibrenation works fine for me now.

P.S. I am using ubuntu 7.10 (gutsy)

---

### Post by natehall on 2007-10-31
Is this a solution for the sceensaver freeze up problem?

---

### Post by Miguelito71 on 2007-11-02
Tried it with my Inspiron 6000 and it fixed nothing.

---

### Post by bluedragon436 on 2007-11-02
Now if only we could find a solution for this same issue on ATI video cards...

---

