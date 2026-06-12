---
title: "xubuntu 22.04 crashes"
date: 2024-07-26
forum: Desktop Environments
---

### Post by maclenin on 2024-07-26
I have experienced two recent (2024) crash/freeze events (22 July and 25 July).

uname-r:
```
6.5.0-44-generic

```
lsb_release -d
```
Description:	Ubuntu 22.04.4 LTS
```

I have 2 SSD (250GB, 1TB) drives and 32 GB of ram on a Z390 M Gigabyte motherboard in the desktop impacted.

1st freeze occurred while using gmail in **Chromium**.

2nd freeze occurred while watching a video in **Chrome**.

2 other browsers were open (but not in focus) at the time: Chrom* and Firefox.

Screen freezes and any video playing freezes with continuous repeat of the last short burst of audio which was playing at the time of the crash.

Keyboard and mouse were rendered inoperable.

Given keyboard (and mouse) deactivation I have been unable to safely reboot using "REISUB".

I have had to perform a hard shutdown both times.

/var/crash/ shows:
```
_usr_lib_xorg_Xorg.0.crash
```
At start-up, I have seen a few power manager related crash messages (since a **clean install of 22.04 in April 2024**), which haven't lead to any noticeable system issues (until, now, perhaps?)

/var/crash/ also shows:
```
_usr_bin_xfce4-power-manager.1000.crash

```
Wondering whether it could be new kernel or Chrom* related?

SSDs seem healthy (via nvme-cli), with 13 unsafe showdowns (11 of these occurring close to previous install end-of-life). I have not checked RAM.

These are the only two crash/freeze events, or problems of any kind, I have experienced with this install.

Thanks for any guidance!

---

### Post by currentshaft on 2024-07-26
Well, did you examine the crash files to see what they indicate? Have you checked journalctl for log messages? Can you reproduce the issue with another window manager?

---

