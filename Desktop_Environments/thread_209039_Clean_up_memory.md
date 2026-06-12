---
title: "Clean up memory?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by dallas7 on 2006-07-04
I'm running Ubuntu 6 since it's release on a P3/866, Intel 815 mobo, with 384MB RAM and a 15GB hard drive.  Connectivity is via 3Mb/s Ethernet.

I don't do much with it; several times a day I'll check email with Thinderbird, surf the Web with Firefox, IM with Gaim and view my graphic files with gThumb.  I also run Firestarter.  I do the updates as they come in.

After a few days, the system will gradually slow down and eventually grind to nearly a halt.  No lockups or crashes, but it becomes unuseable.

When I shut down all apps and open System Monitor, it reports that 80.5% of RAM and 46% of my 619MB swapfile is in use.

When I restart, those numbers are 21% and 0%.

I'm not all that Linux/Ubuntu savvy and I've searched for info on memory management to no avail.

What's resident in Ubuntu or what's available that's supported that will let me refresh memory without a restart?

Thank you.

---

### Post by Jason_25 on 2006-07-04
Try increasing your swapfile size to a gig if you can.  Run memtest too if you haven't lately.  Kubuntu uses less ram with KDE.

---

### Post by Ramses de Norre on 2006-07-04
Restarting X could help a lot too, to do so execute ```
sudo /etc/init.d/gdm restart
``` or press ctrl+alt+backspace.

---

### Post by kinematic on 2006-07-04
a linux box actually uses almost all of the ram available as disk cache because it would just go to waste if it's not used.
in a "normal" situation it's much faster to start program's or acces memory from disk cache.

---

