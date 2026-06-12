---
title: "I Can't Get my mouse to work any more?????HELP ME PLZ"
date: 2006-01-26
forum: Desktop Environments
---

### Post by gamemaster357 on 2006-01-26
i had been using mplayer to play a mpeg 4 and then all of a sudden the player freezes.....i couldnt exit....so i restarted my pc and everything seemed to be fine.....except the mouse....the optical light was on but it wouldnt move any more...can someone please help me...im kinda new to the linux community..

---

### Post by FarEast on 2006-01-27
Press [ctl]+[Alt]+[F1] and log on the system.
Type 'lsmod | grep hid'.
If 'usbhid' is not loaded, type 'sudo modprobe usbhid'.
Type 'exit' and press [ctl]+[Alt]+[F7] to go back to the window manager.
I hope this helps:).

---

### Post by gamemaster357 on 2006-01-27
thx

---

