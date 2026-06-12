---
title: "Dell studio 1536 usb ports not detected"
date: 2011-04-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jdelgado08 on 2011-04-06
Hey guys,

I'm new to the site, as well as pretty much of a noob when it comes to Linux...
I recently installed Ubuntu 10.10 on my Dell Studio 1536 Laptop and although automount is enabled to true, Ubuntu does not detect anything inserted into the usb ports.

Here is the output of fdisk -l

I've been looking around for an answer and have not come to any conclusion or found any answer
```
jr@ubuntu:~$ sudo fdisk -l
[sudo] password for jr: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd3fd54c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
/dev/sda3   *        1280       38914   302290037+   7  HPFS/NTFS

```

It detects nothing and lsusb does nothing as well.
At first I guessed it was just not detecting my USB Flash Drive, but when I inserted my WD External HDD it wasn't detected either.

Any help would be appreciated. Thanks

---

### Post by mikewhatever on 2011-04-06
Lsusb is not supposed to do anything other then produce an output. Is there no output at all?

---

### Post by advs89 on 2011-04-22
I'm not the original poster, but I have a Dell Studio 1536 and I'm having the exact same problem.  I'm running Kubuntu 10.10.

External Logitech wireless usb keyboard doesn't work, external Microsoft wireless mouse doen't work, flash drives don't work...

It looks like the original poster hasn't responded in two weeks, but maybe he or she figured out the problem and can tell us how it was fixed.

Here is the output of the commands you mentioned:

```
adam@ubuntu:~$ sudo lsusb
[sudo] password for adam: 
adam@ubuntu:~$ fdisk -l
adam@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1966    15728640    7  HPFS/NTFS
/dev/sda3   *        1966       38914   296784896    7  HPFS/NTFS

```

Notice the lack of output from lsusb... I've also tried booting with "acpi=force irqpoll" and also tried adding "usbhid" and "hid" to "/etc/modules" with no success.

Any help at all would be greatly appreciated.

---

### Post by jdelgado08 on 2011-04-22
> **mikewhatever said:**
> Lsusb is not supposed to do anything other then produce an output. Is there no output at all?

Sorry for the late reply, i've been busy with school.
Finals are just around the corner, but anyways to answer your question.
No lsusb produces no output what so ever.

For the time being i'm just using Ubuntu 10.10 on VMWare on my Dell Vostro.

---

### Post by advs89 on 2011-04-24
Just an update, but I just now tried opensuse to see if the problem was specific to (K)Ubuntu and it didn't work with that either.

---

### Post by advs89 on 2011-04-25
I actually have it working now.  I found the exact bug on the Ubuntu launchpad tracker and they have a workaround at that [site]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/647043").

You have to add "pci=nocrs" (without quotes) to the GRUB2 parameters.

Here's what I did.
[LIST=1]
[*]Open a terminal
[*]```
cd /etc/default/
```
[*]```
sudo gedit grub
```
[*]Include "pci=nocrs" in GRUB_CMDLINE_LINUX=""
[*]Open a new terminal
[*]```
sudo update-grub
```
[*]And then restart the computer
[/LIST]

You could probably try it temporarily by editing the boot parameters on startup (although that didn't work for me - it may have been a typo, though)

---

