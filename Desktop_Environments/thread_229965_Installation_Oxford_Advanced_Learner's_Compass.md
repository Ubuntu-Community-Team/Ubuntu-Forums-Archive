---
title: "Installation Oxford Advanced Learner's Compass"
date: 2006-08-05
forum: Desktop Environments
---

### Post by radian on 2006-08-05
Hi,
I tried to install "Oxford Advanced Learner's Compass" on Ubuntu 6.06, but I receive error:
```

sudo sh /media/cdrom0/linux/installation.sh
Verifying archive integrity... All good.
Uncompressing ..........................
/home/adrian/.setup5544: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Couldn't load 'atal'
The setup program seems to have failed on x86/glibc-2.1

Please contact Loki Technical Support at support@lokigames.com
The program returned an error code (1) 

```
Anyone know how to install this dictionary on Ubuntu?
PS. I installed "Oxford Advanced Learner's Compass" on SLAX 5.1.4 KillBill Edition without errors.

---

### Post by radian on 2006-08-05
Problem resolved: I just had to install libgtk1.2 :p

---

