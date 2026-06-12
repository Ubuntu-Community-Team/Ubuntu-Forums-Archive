---
title: "EMERGENCY! Cant reinstall Ubuntu"
date: 2006-05-02
forum: Desktop Environments
---

### Post by linuxNewb on 2006-05-02
I have been running Ubunut on my Presario latop for over a year with no problems; Wart, Hoary, now Breezy. Yesterday I tried to open nautilus, and the computer seemed to freeze (icons disappeared). I manually powered down, and rebooted. Ubuntu wouldn't boot, it said the hard-drive was mounted read only, and that I needed to run e2fsck. I ran e2fsck as instructed, and got a bunch of errors. Ubuntu still would't boot. So I tried to reinstall (I have duall-boot with windows -- windows still runs fine.) I select to format the ubuntu partition and use it as '/' and I set the boot-flag to it, I already sees and labels the swap drive. But then, EVERY TIME it gets to installing the Base system, it fails. It says

debootstrap exited with an error, failed to: Install the Base System

Please help! I've been on this since yesterday, and I have a project due the end of this week (I was already behind), that requires linux. Thanks in advance.

---

### Post by olsonar on 2006-05-02
try using the partitioner to delete the partition first, then create an identical one in its place. Also, try cleaning your cd, or burn a new one.

---

### Post by tsrjzq on 2006-05-03
[QUOTE=olsonar]try using the partitioner to delete the partition first, then create an identical one in its place. Also, try cleaning your cd, or burn a new one.[/QUOTE]
yes, this may be a good choice, btw, for linux, try to shutdown or reboot it by press the reset button, is so bad. for example, nautilus or X has no response, you can kill it in ttys, not reboot it. reboot is more like the actions in windows. No need in linux.

---

### Post by olsonar on 2006-05-03
[quote=tsrjzq]btw, for linux, try to shutdown or reboot it by press the reset button, is so bad. for example, nautilus or X has no response, you can kill it in ttys, not reboot it. reboot is more like the actions in windows. No need in linux.[/quote] 
yes, that's a good idea. even if the GUI won't come back, you can reboot from the command line with "sudo reboot". the key combo to kill X is Crtl+Alt+Backspace.

---

