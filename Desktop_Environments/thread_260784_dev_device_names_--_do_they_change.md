---
title: "/dev device names -- do they change?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Locke2053 on 2006-09-19
How are the device names (hda, sda, md0, etc.) assigned to physical devices in /dev?

For example, suppose you have a PCI SATA controller with 2 disks. Linux creates devices sda and sdb for those disks automatically when you boot.

Then, you add another PCI SATA controller with 2 more disks.

When you boot, will the 2 disks on the old SATA controller still be called sda and sdb, with the new ones sdc and sdd? Or is there a possibility that they the disks on the new controller could take over the names sda and sdb?

I'm building a RAID server, and I will be growing it with new PCI SATA controllers and disks as I get my hands on them. If the names of my disks in /dev change every time I add a SATA controller, it could cause some serious problems...

---

### Post by nereid on 2006-09-19
The names should not change. To be on the save side you can specify the device names in the udev configuration.

---

### Post by Locke2053 on 2006-09-19
How do I do this? In /etc/udev/rules.d/65-persistent-device-names ? Do I need to create a new file in rules.d?

That config file syntax is heinous.

The last time I did something like this was in the mknod days. My, have things changed.

---

### Post by nereid on 2006-09-20
Follow this [link](http://ubuntuguide.org/wiki/Dapper#How_to_configure_PalmOS_Devices) for an exampe for a PalmOS device. Maybe it helps.

---

