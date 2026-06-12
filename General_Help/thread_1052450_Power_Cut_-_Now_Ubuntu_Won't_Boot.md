---
title: "Power Cut - Now Ubuntu Won't Boot"
date: 2009-01-27
forum: General Help
---

### Post by jonno on 2009-01-27
Help! Last night we had a power outage while I was using my Ubuntu Intrepid system and since then the system won't boot. I don't know where to start.

Grub runs ok but then I never see the Ubuntu login screen. If I press the Ctrl key (lucky guess) I see:
```
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
     - Boot args (cat /proc/cmdline)
            - Check rootdelay= (did the system wait long enough?)
            - Check root= (did the system wait for the right device?)
     - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/......... does not exist. Dropping to a shell!

Busybox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands
```

Grub is installed on the hdd I'm pretty sure so the hdd must be at least partially functional. Somewhere along the boot path something must have gotten corrupted. I don't really understand the whole boot process very well so any pointers would be good.

Is there a way to turn on the display of commands/messages during boot. I guess Ubuntu hides these by default.

I'm currently downloading the Ubuntu LiveCD via my laptop so I can troubleshoot the drive but to be honest I don't know where to start.

Edit: Never mind. I found a whole bunch of other threads dealing with this. Thread can be closed.

---

### Post by fragos on 2009-01-28
The power loss may have corrupted data on your disk because it was writing when the power loss occured or because it hadn't flushed it write buffers before the failure. I suggest you boot from an Ubuntu CD and when installing look for the option to repair your system. If that doesn't work, reinstall may be your best option.

---

### Post by jonno on 2009-01-28
Thanks, I didn't know there was a repair option on the LiveCD. I'll check it out.

I found some threads when searching on the "Gave up waiting for root device" and found that I can boot by typing exit. [Some have suggested]("http://ubuntuforums.org/showthread.php?t=1027432&highlight=gave+waiting") that the system wasn't waiting long enough before trying to start the system. The suggested workaround is adding a rootdelay command but that doesn't seem to have worked for almost everyone (including me).

---

### Post by icanfly0307 on 2009-01-28
When you are dropped to the shell prompt, try typing fschk. That should fix your hard drive and its errors.

---

### Post by jonno on 2009-01-28
So tonight I did a bunch of updates including a kernel update. I rebooted and all is well!

---

