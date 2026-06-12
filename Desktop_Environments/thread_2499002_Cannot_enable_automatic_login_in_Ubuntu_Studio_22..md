---
title: "Cannot enable automatic login in Ubuntu Studio 22.04"
date: 2024-07-07
forum: Desktop Environments
---

### Post by allelopath on 2024-07-07
I have set to autologin in sddm.conf and in the Settings > Startup and Shutdown > Login Screen (SDDM)
What am I missing?

>>cat /etc/X11/default-display-manager
/usr/bin/sddm

/etc/sddm.conf
  Session=Ubuntu
  [Autologin]
  User=allelopath


System Settings - User
Name: Al Lelopath
Username: allelopath
Account type: Administrator

Settings > Startup and Shutdown > Login Screen (SDDM)
  Automatically log in: <check> as user : allelopath with session Plasma (X11)

Ubuntu Studio 22.04

KDE Plasma Version: 5.24.7
KDE Frameworks Version: 5.92.0
Qt Version: 5.15.3
Kernel version: 6.5.0-42-lowlatency (64 bit)
Graphics Platform: X11

Hardware
Processors: 4 x Intel Core i5-4590 CPU @3.3GHz
Memory: 7.7 GiB of Ram 
Graphics Processor: Mesa Intel HD Graphics 4600

---

