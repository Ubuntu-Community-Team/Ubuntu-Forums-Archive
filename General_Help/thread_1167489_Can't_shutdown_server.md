---
title: "Can't shutdown server"
date: 2009-05-22
forum: General Help
---

### Post by japtar10101 on 2009-05-22
I have an ubuntu server that, if I run, "sudo shutdown -hP now", it'll attempt to power off, then throw an error and halt.  After that, the system become unresponsive and never turns off.

I'll check the error message error again next time I put the server on, but basically, it goes along the lines of, "Can't find IDE drive, system halting".  This occurs both on shutdown and reboot.

---

### Post by japtar10101 on 2009-05-23
The error message goes as follows:
```

$ shutdown -hP now
* stopping ClamAV
* stopping MySQL
* Saving system clock
* Asking all remaining processes to terminate
* All process ended within 2 seconds
* Deconfiguring network interfaces
* Deactivating swap
* Unmounting local filesystems
* Will now halt
halt: Unable to iterate IDE devices: no such file or directory
[182.820656] System halted.

```
Kind of strange it unmounts the filesystem first, then throws the error there's no file/directory.

---

### Post by rkdwv on 2011-01-09
Same problem here. On shutdown -h now ubuntu server 10.10 just halts with no errors. Reboot command works. What can I try to solve this problem?

---

### Post by mdlueck on 2011-01-09
For us at one point server 9.10 would crash when executing poweroff but was just fine shutting down with reboot. We would issue reboot, press a key at the Grub screen once rebooted, then poweroff the server. Problem has gone away since the upgrade to 10.04 LTS.

"segmentation fault on shutdown caused by new 2.6.31-21 clockevents.c"
[https://bugs.launchpad.net/bugs/574899](https://bugs.launchpad.net/bugs/574899)

Sounds like the same sort of thing to me, perhaps? Perhaps the same work-around will work for you.

---

