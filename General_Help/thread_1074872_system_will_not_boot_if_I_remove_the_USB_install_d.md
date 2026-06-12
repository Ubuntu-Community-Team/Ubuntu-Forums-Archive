---
title: "system will not boot if I remove the USB install disk?"
date: 2009-02-19
forum: General Help
---

### Post by rasta_caleb on 2009-02-19
I installed Ubuntu server 8.10 via a USB key

Everything installed is working fine (on this hardware: [http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html](http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html))

However, the system will not boot if I remove the USB install disk.

I tried grub-install to the location of my real HD, but it still boots up w/ an empty screen.  If I put the USB key in and tell the bios to boot from it, it works fine.  I can also remove the USB key once the boot has occurred, and the os and everything seems to work fine still.

Please help


Thank you

---

### Post by dcstar on 2009-02-19
> **rasta_caleb said:**
> I installed Ubuntu server 8.10 via a USB key

Everything installed is working fine (on this hardware: [http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html](http://www.surpluscomputers.com/348232/rackable-systems-dual-xeon-3.0ghz.html))

However, the system will not boot if I remove the USB install disk.

I tried grub-install to the location of my real HD, but it still boots up w/ an empty screen.  If I put the USB key in and tell the bios to boot from it, it works fine.  I can also remove the USB key once the boot has occurred, and the os and everything seems to work fine still.

Please help


Thank you

Probably the Grub boot stuff didn't install properly, do a forum search for restoring Grub and you should get details for fixing it.

---

### Post by ajgreeny on 2009-02-19
I think the problem is that grub is on your hard disk, but the grub menu list file (boot/grub/menu.lst) is on the usb drive.  If that is not found you will always have that problem.  You either need a separate /boot partition with all the grub files on, including the menu.lst, or if you have a dual boot you need to put grub on the usb drive, not the hard disk, and set the machine to boot first from the usb, second from the hard disk.  You should also restore the windows MBR to the hard disk, so that the machine boots straight to windows if the usb drive is not atttached, but when it is attached it will go to grub and offer you the choice.

EDIT:  Sorry but I think I misunderstood.  Did you install to a usb drive or from it?  I assumes thenformer, but now think I got that wrong.  However, if I did get it right first time, then my post is still relevant; your problem is the placing of the grub config files ie, /boot/grub/menu.lst

---

### Post by rasta_caleb on 2009-02-23
Thanks for the help :-)

I got it working, using these steps:

1. I booted from the usb drive but hit esc during the boot so I could jump into recovery mode.

2. I went to the root command line

3. ran fdisk -l which gave me a list of drives.  I could tell by the size which one was the partition I setup as /boot during install (/dev/sdb5)

4. ran grub-install /dev/sdb5

5. had to change my device.map file, it still had the wrong entry for hd0

6. rebooted, without the key, system started ... w00t!&#9830;

---

