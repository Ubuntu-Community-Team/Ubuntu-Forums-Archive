---
title: "slow boot with gutsy? switch back to feisty kernel!"
date: 2007-10-31
forum: Desktop Environments
---

### Post by suoko on 2007-10-31
I just switched back to feisty kernel 2.6.20 on my gutsy and now my laptop is as fast as feisty
And everything works!

EDIT:
the only thing which doesn't work is freq scaling  but it's ok for now: the system is more responding :-)

DMESG errors for freq scaling:
 acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   21.321106] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   21.321223] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   21.321281] acpi_cpufreq: Unknown symbol acpi_processor_register_performance

I'd like to solve this problem but I can happily live with it

By the way:I have no slow boot problems with gutsy kernel on my single core desktop

UPDATE: 
usb ports do not work with feisty kernel [wireless and firewire work] :-(
I can't do any video editing with GUTSY kernel due to poor performances!

---

### Post by suoko on 2007-11-15
I just found out what's causing the slow boot of gusty kernel (and a slow machine overall):

in order to avoid my disks be recognised as SATA (since that caused the issue reported in below links) I disabled many modules as suggested in the launchpad/bug page.
However f I reenable those modules the boot goes fast BUT the bug of drives recognized as sata (and consequent random hang of the disks) reappears.

PLEASE HELP ME (as well as all other bugged users)

see thread: [http://ubuntuforums.org/showthread.php?t=493844](http://ubuntuforums.org/showthread.php?t=493844)
see bug: [https://bugs.launchpad.net/ubuntu/+bug/104581](https://bugs.launchpad.net/ubuntu/+bug/104581)

List of modules I disable in /etc/initramfs-tools/modules file:

```
piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod
```

Just noticed that while the pc hangs, the CPU goes 100%

---

### Post by Cammy on 2007-11-15
subscribing...

My laptop takes like 5 full minutes to boot.  Once it's up, no problem, but waiting for the boot up (or reboot) is agonizing.

---

### Post by Cammy on 2007-11-16
There was a huge gutsy update last night that my laptop spend like 20+ minute downloading and installing.  Now it boots as fast as my desktop (with Dapper) so I guess they must've solved something.

---

### Post by suoko on 2007-11-17
Solutions:
1) keep a CD-ROM or a DVD-ROM in your DVD drive.
2) upgrade DVD firmware (see [https://bugs.launchpad.net/linux/+bug/75295/comments/97](https://bugs.launchpad.net/linux/+bug/75295/comments/97))
3) kill hald-addon-storage

(see also kernel bug [http://bugzilla.kernel.org/show_bug.cgi?id=8316](http://bugzilla.kernel.org/show_bug.cgi?id=8316) for more info)

At this moment I can say point 1 do work as a solution. I'll try point 2 in a while and let you know.
Point 3 is not a solution.

UPDATE:
point 2 works and solves the problem

---

