---
title: "CD does not mount - Slow boot"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Patb on 2005-12-17
Hi.  A small problem with my desktop: About once in every 5-6 boots, the indicator light on the CD-RW drive keeps blinking during boot (normally it is blinks a few times during the BIOS stage then goes off) The Ubuntu boot reverts to the full text mode instead of the normal graphic mode.  After some delay Ubuntu starts but the CD is not mounted.  Does anyone have any suggestions on what is causing this or what diagnostic steps I might take.  Thanks, Pat.

---

### Post by savas on 2005-12-17
Hi friend. I am suffering from same problem for at least one year. But i could not find any solution to this problem. I think, a hardware problem causes to this problem. I think this way because of it is not stable(it's happening one time for a week). But i am not sure, if i never boot to windows XP this problem never occures(at least for a long time). If you find any solution, please let me know. Good luck.

---

### Post by Patb on 2005-12-17
Thanks for the sympathy, Savas.  The problem recurred just now after booting on Win98.  I also forgot to say that the relevant line from my /etc/fstab reads:
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
If anyone has any suggestions, I would be very grateful.  Cheers. Pat.

---

