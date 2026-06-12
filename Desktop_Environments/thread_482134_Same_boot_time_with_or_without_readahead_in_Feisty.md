---
title: "Same boot time with or without readahead in Feisty?"
date: 2007-06-23
forum: Desktop Environments
---

### Post by MichaelOpdenacker on 2007-06-23
Hello,

I'm using Ubuntu Feisty on my x86 laptop. I'm surprised to observe that readahead doesn't seem to have any impact on bootime (on my case at least), while I could observe a 17% boot time reduction with Edgy!

To measure the impact of readahead, I added the following lines to /etc/init.d/rmnologin:

echo `uptime` > /var/log/boottime
cat /proc/uptime >> /var/log/boottime

With readahead (default), I get a boot time of 31.46 s:
12:51:55 up 0 min, 0 users, load average: 1.36, 0.36, 0.12
31.46 18.70

Without readahead (renaming /sbin/readahead-list), the boot time is almost identical: 31.81s
12:58:42 up 0 min, 0 users, load average: 1.45, 0.37, 0.12
31.81 18.96

When I did the same tests on Ubuntu Edgy, here's what I got:

Without readahead:
15:16:56 up 0 min, 0 users, load average: 1.31, 0.35, 0.12
45.83 28.68

With readahead:
15:20:18 up 0 min, 0 users, load average: 0.96, 0.24, 0.08
37.75 23.10

Could you confirm that readahead reduces your boot time in Feisty (just rename /sbin/readahead-list or /etc/readahead/boot)? This way I'll know if there's something broken on my side (don't see what so far... "/etc/init.d/readahead start" actually does something when I run it manually) :-|

Thanks in advance,

Michael.

---

