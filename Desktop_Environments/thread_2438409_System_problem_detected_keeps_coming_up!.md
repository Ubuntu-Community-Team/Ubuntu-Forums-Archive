---
title: "System problem detected keeps coming up!"
date: 2020-03-11
forum: Desktop Environments
---

### Post by williepabon on 2020-03-11
Hi!

This is a problems that I've been having for a few weeks, and the solutions given elsewhere have not been of much help. This is a picture of the message:

[https://drive.google.com/file/d/1h74lEY_y9WjJSGMDqiYl06PvVlET2R-Y/view?usp=sharing](https://drive.google.com/file/d/1h74lEY_y9WjJSGMDqiYl06PvVlET2R-Y/view?usp=sharing)

Clicking report problem is of no help. I've been suggested to erase the problem file:

williepabon@williepabon-Macmini:~$ ls -l /var/crash/
total 21008
-rw-r----- 1 gdm whoopsie 21512098 Mar 11 12:06 _usr_bin_gnome-shell.121.crash

williepabon@williepabon-Macmini:~$ sudo rm /var/crash/*
[sudo] password for williepabon: 

The file was erased but, when I reboot the following day, it comes up again.
I have also been suggested to run a full package upgrade:

sudo apt update && sudo apt full-upgrade

The problem keeps coming up. Here is the information about my machine.

williepabon@williepabon-Macmini:~$ uname -a
Linux williepabon-Macmini 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

williepabon@williepabon-Macmini:~$ lsb_release -crid
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic
williepabon@williepabon-Macmini:~$

Any help to solve this will be really appreciated. Thanks.

---

### Post by webaake on 2020-03-12
It's the app Apport which is doing this and you can disable it. Check here: [https://vitux.com/how-to-disable-enable-automatic-error-reporting-in-ubuntu-18-04-lts/](https://vitux.com/how-to-disable-enable-automatic-error-reporting-in-ubuntu-18-04-lts/)

The error reporting seems sometimes arbitrary and it appears to report minor problems like miniscule internal problems in themes and stuff. Mostly annoying. It's better to check for problems manually like with dmesg and going thru .xession-errors and the logs in /var/log.

---

### Post by williepabon on 2020-03-12
Thank you **webaake**, you solved my problem.

---

### Post by webaake on 2020-03-13
:)

---

### Post by webaake on 2020-03-21
OOps! Seems that I gave some Old School advice about logs. Today it's journalctl and systemd that rules the world. Some useful commands:
```
journalctl -r 
journalctl -r | grep -i error
journalctl -r | grep -i failed
```

-r is for reverse so you'll get the newest entries first. The log can be huge to scroll in!

grep -i is for search words without regard to capital letters. It hits "Nvidia" and "nvidia" and so on.

---

