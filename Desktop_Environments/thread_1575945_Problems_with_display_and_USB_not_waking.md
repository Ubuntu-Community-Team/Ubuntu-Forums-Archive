---
title: "Problems with display and USB not waking"
date: 2010-09-16
forum: Desktop Environments
---

### Post by gamer_pro_2000 on 2010-09-16
Alright guys.  I recently started operating as the admin of a private school and I'm trying to track down a problem with the machines.  We operate for instances of X Server per workstation, one per monitor, keyboard, and mouse, so we have one computer with four video cards running four screens.  The USB keyboards, mice, and the HDMI monitors have all been statically assigned in Xorg.  What I need to figure out is why sometimes when the monitors and usb devices go to sleep, sometimes they won't wake up.  3/4 of the monitors, keyboards, and mice will, but one of them won't, necessitating a reboot.  Any ideas?

---

### Post by gamer_pro_2000 on 2010-09-17
*BUMP*
Still haven't got an answer to this one from posting it yesterday.  Does no one have an idea or do you guys want a specific log file from when it occurs?

---

### Post by Jerubaal on 2010-09-17
I'm getting the same problem, but only recently.

EDIT: So I found the problem - I had enabled something in the BIOS to do with putting the pc in standby when the monitor went to sleep....

---

