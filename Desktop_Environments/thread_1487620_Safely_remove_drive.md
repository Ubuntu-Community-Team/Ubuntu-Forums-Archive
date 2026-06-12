---
title: "Safely remove drive"
date: 2010-05-19
forum: Desktop Environments
---

### Post by Pengwyn44 on 2010-05-19
I am using Ubuntu 10.04 lucid lynx. I have two usb external hard drives.
Both of them unmounted via the GUI on 9.04. Now one does and the other does not. The one that does not does unmount via the command line without any error message. When unmounted via the GUI I get the error message:

UNABLE TO STOP DRIVE
Error detaching: helper exited with exit code 1: Detaching device /dev/sdd
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.3)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

Can anyone suggest a reason for this please?

---

### Post by Claus7 on 2011-01-16
Hello,

having come across this post, I add the following:

I got the same error when plugging and unplugging a usb hdd fat32 on ubuntu maverick 10.10. The hdd was both formatted with maverick or hardy heron. I do not face problems with hdd formatted with linux journaling. 

From here:
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/571194)
and here:
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/466575)

is supposed to be a duplicate bug (maybe of nautilus..?) still till the time of writing.

I do not face problems with command line (sudo eject /dev/sdb) or detaching it from hardy heron.

Regards!

---

### Post by slowwound on 2011-05-22
i have the same problem in maverick.

is there a solution yet ?

---

### Post by Copper Bezel on 2011-05-22
Beyond just unplugging the flash drive? I've found that to be 100% effective at unmounting drives. = ) 

The bugs listed haven't been fixed, obviously. You can determine whether or not it's a Nautilus-specific problem by running umount /media/[the device's label] .

---

### Post by xadder on 2011-05-22
I've been having similar problems since 10.10. Now I usually have to do:

sudo eject /dev/sdb1  

... or whatever dev is mounted. Very odd that Ububtu requires such kludges for such a basic thing.

---

