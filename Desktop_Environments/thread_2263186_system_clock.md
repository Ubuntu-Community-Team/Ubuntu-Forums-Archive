---
title: "system clock"
date: 2015-01-30
forum: Desktop Environments
---

### Post by jimbo10 on 2015-01-30
[FONT=times new roman][SIZE=4]i have dual-boot Windows Vista (ultimate) & UBUNTU 14.04;

the system clock(s) have, recently, been going out-of-whack.....

the one on UBUNTU is abt 24hrs behind the one on Win Vst;

when i change one, the other goes out of whack, some-how......

previously, i tried changing system clock in the BIOS but, now, i can't seem to access that feature......

any help much appreciated, as always!

thnx [/SIZE][/FONT]):P

---

### Post by Impavidus on 2015-01-30
Well, we often see that Windows interprets the system clock as local time and Linux as UTC, but there are no time zones with a 24 hour difference from UTC, so I'm a bit puzzled. Could you show the contents of the file **/etc/default/rcS** and tell us in what timezone you are?

---

### Post by jimbo10 on 2015-01-30
> **Impavidus said:**
> Well, we often see that Windows interprets the system clock as local time and Linux as UTC, but there are no time zones with a 24 hour difference from UTC, so I'm a bit puzzled. Could you show the contents of the file **/etc/default/rcS** and tell us in what timezone you are?

hmmm.....i wonder if that's the problem.....in which case: Linux would always be showing the correct time, eh?
the time-zone is UTC+10;

i will check out that file and post later......

thnx!

---

### Post by opodaniel-x on 2015-03-10
Same problem here with Xubuntu 14.04
in /etc/rcS   i have UTC=no
but when I change time, the system will also change bios time to UTC. This is not an issue( except that will mess Windows 7 time ).
more /etc/localtime will produce  Asia/Taipei
date shows corect time but the clock widget from taskbar shows a 2 hours difference :D :(.[IMG]http://forum.softpedia.com/index.php?app=core&module=attach&section=attach&attach_rel_module=post&attach_id=1453536[/IMG]

---

