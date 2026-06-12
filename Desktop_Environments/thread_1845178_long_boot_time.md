---
title: "long boot time"
date: 2011-09-16
forum: Desktop Environments
---

### Post by pratikk on 2011-09-16
XFCE/Xubuntu loads funny for me -- in over two minutes. The desktop appears quickly but the system isn't actually available. Nothing works. The panel shows only the power manager icon, no network icon or other icons I've added. The HDD LED stays dead for about 30 seconds, then the power icon flashes about 10 times (not the whole desktop, not visibly), the HDD finally turns and then the system actually becomes available. Total: two huge minutes, same as Vista. 

I use most of the available Ubuntu desktops according to my mood and all but XFCE/Xubuntu boot quickly as advertised. I can't see any obvious problems in the bootlog, so is there is a desktop-specific log I should look at? I'd like to solve this because I like XFCE a lot.

---

### Post by Toz on 2011-09-17
Try having a look at ~/.xsession-errors - there might be something there.

---

### Post by Rubi1200 on 2011-09-18
Please post the specifications for the computer and you can also look in the following logs for indications of what might be happening; dmesg and syslog.

---

### Post by pratikk on 2011-09-18
This is kind of embarrassing but right after I posted that, XFCE began to boot in a flash, for the first time since I installed it six months ago. It's almost as fast as Fluxbox. In the interim, I had shifted back to Gnome and made two changes: set IBus to launch at startup and installed the CPU frequency scaling applet. Maybe IBus made the difference? I looked in the logs suggested and IBus-related errors have disappeared. There were a few earlier.

Rubi: this is a 1005HA EEEPC dual-booted with XP, running a regular Lucid install with all major desktops installed, out of curiosity.

---

### Post by mörgæs on 2011-09-18
If the problem is solved, please mark the thread so using 'thread tools'.

---

