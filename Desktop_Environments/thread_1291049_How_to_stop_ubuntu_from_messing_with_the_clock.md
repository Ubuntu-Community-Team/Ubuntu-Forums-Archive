---
title: "How to stop ubuntu from messing with the clock?"
date: 2009-10-14
forum: Desktop Environments
---

### Post by ohadbasan on 2009-10-14
Hey guys

I'm dual booting ubuntu karmic beta and arch linux.
I don't know why but if I boot arch after booting ubuntu, arch throws a message "superblock last write time is in the future" and forces me to fsck.
I've been told on linuxquestions.org that ubuntu does something to the clock that causes it. (I don't really know what,maybe changes it)
does someone know how to fix that?

10x!

---

### Post by mcduck on 2009-10-14
Both operating systems write their time back to your computer's CMOS clock when you shut them down. But the difference is in what time they use, the traditional way for all Unix/Linux systems is to keep the CMOS clock running at UTC time and only display local time to the users. However latest Ubuntu versions default to using local time for the CMOS clock as well because that avoids time changing when dualbooting with Windows, as Windows always assumes the CMOS clock to be in local time.

You can change the tie setting in which ever OS you want, either set Ubutnu to use TC time or Arch to use local time.

To change the setting in Ubuntu you need to edit /etc/default/rcS file and change "UTC=no" to "UTC=yes".

Using UTC as CMOS time makes changing the local time zone and switching between daylight saving time and normal time easier (because the system time doesn't need to be changed at all), but it doesn't work when dualbooting with Windows.

---

### Post by ohadbasan on 2009-10-15
Thanks!
works like a charm!

---

