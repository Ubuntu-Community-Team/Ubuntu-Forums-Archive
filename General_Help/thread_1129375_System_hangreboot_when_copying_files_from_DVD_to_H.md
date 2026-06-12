---
title: "System hang/reboot when copying files from DVD to HD"
date: 2009-04-18
forum: General Help
---

### Post by frecon on 2009-04-18
I was copying files from a DVD to my hard drive when suddenly everything hanged. Everything on the screen freezed and both the keyboard and the mouse didn't work. I waited a few minutes but when nothing happened I hard rebooted my laptop (Dell m1330). Then I tried to copy the files again but it hanged. But this time it rebooted it self after approx. 30 seconds. 

Why is this happening? How can I determine what kind of problem I have? Are there any log files I can check? Thanks in advance for your help.

OS: Ubuntu 8.10

---

### Post by justin_guerin on 2009-04-18
Check the log files in /var/log, especially /var/log/messages and /var/log/dmesg.  /var/log/syslog and /var/log/Xorg.0.log are worth looking at as well.

---

### Post by dcstar on 2009-04-18
> **frecon said:**
> I was copying files from a DVD to my hard drive when suddenly everything hanged. Everything on the screen freezed and both the keyboard and the mouse didn't work. I waited a few minutes but when nothing happened I hard rebooted my laptop (Dell m1330). Then I tried to copy the files again but it hanged. But this time it rebooted it self after approx. 30 seconds. 

Why is this happening? How can I determine what kind of problem I have? Are there any log files I can check? Thanks in advance for your help.

OS: Ubuntu 8.10

Did you run out of disk space and fill your root partition?

---

