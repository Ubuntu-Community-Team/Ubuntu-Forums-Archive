---
title: "Cant set Wake on Alarm in Mate 16.04"
date: 2016-08-04
forum: Desktop Environments
---

### Post by mister_p_1998 on 2016-08-04
Hi guys,
I recently upgraded my aging Ubuntu 8.04 to Mate 16.04, and Im finding I now cant change the wake on Alarm settings, its currently set to around 06:30 am, but whenever I try to write the new time back (I want to change to 14:30) , it wont seem to accept the changes.
sudo sh -c 'echo "00-00-00 14:30:00" > /sys/class/rtc/rtc0/wakealarm'
Is it a 16.04 thing? or is there something I can fix? I use 10.04 at work and that seems fine.

TIA
Steve

---

