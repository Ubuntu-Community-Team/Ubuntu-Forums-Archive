---
title: "I may have a problem with the kernel"
date: 2008-03-04
forum: Desktop Environments
---

### Post by arielsegal on 2008-03-04
Hi,
I'm using Ubunto 7.10 . While working on my machine, it suddenly froze. I had to do a hard reset. After reboot, I had no Internet and no audio. I'm connected to the Internet with a USB wireless wifi stick that uses an rt73 driver. I'm attaching the /var/log/messages file that was prodeuced right after the boot.
I'm especially concerned with the beginning  lines:
> Mar  4 09:15:37 segal syslogd 1.4.1#21ubuntu3: restart.
Mar  4 09:15:37 segal kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar  4 09:15:37 segal kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar  4 09:15:37 segal kernel: Symbols match kernel version 2.6.22.
Mar  4 09:15:37 segal kernel: No module symbols loaded - kernel modules not enabled.
Mar  4 09:15:37 segal kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
How do solve my problem?

---

### Post by arielsegal on 2008-03-04
here is attached file

---

