---
title: "Wake on Lan from S3 suspend not working (Power button fine, wol from S4 fine)"
date: 2006-09-03
forum: Desktop Environments
---

### Post by marplar on 2006-09-03
Hello,

When I try to wakeup my 6.06 machine from suspend (S3 sleep state) using WOL the computer powers up (fans come on) but nothing else. Nothing is displayed on the screen, no power to USB keyboard/mouse and no access to SMB shares. I have to power off and reboot.

If I hibernate to S4, or shutdown to S5 then WOL works fine. I can also wakeup from S3 by pressing the power button without any problem.

As far as I can tell the log files are not updated at all during the failed wakeup. I have tried to resolve this by using the commands *ethtool -s eth0 wol g* and *echo NMAC > /proc/acpi/wakeup* but it does make any difference. My hardware is Nforce 4.

Any help would be appreciated!

---

### Post by marplar on 2006-10-02
This problem went away after I installed the 2.6.18 kernel.

Maybe related to this: [http://bugzilla.kernel.org/show_bug.cgi?id=6881](http://bugzilla.kernel.org/show_bug.cgi?id=6881)

---

