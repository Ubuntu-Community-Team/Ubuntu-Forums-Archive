---
title: "GRUB - Error 17"
date: 2006-03-02
forum: Desktop Environments
---

### Post by jimmymac on 2006-03-02
Hi,

I installed ubuntu 5.1 dual booting with XPP.  The whole idea was learn to use linux while still being able to get some work done.  
Anyhow, I deleted a data partition as I had gotton an external HDD.
Now when I boot up I get Error 17 as the grub trys to load.  

Any ideas?

TIA

Jimmy

---

### Post by mlind on 2006-03-02
Did you make backup of GRUB on floppy?

I've done same myself too numerous times but if you can access
grub shell, problem is easier to fix. If not, you can use rescue cd to boot
on your Ubuntu and assign run "update-grub".

Two good threads that might help
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Irony on 2006-03-02
Boot from the install ubuntu CD and at the prompt type;

[PHP]boot: rescue[/PHP]

Go to a  mount point, Ubuntu is on hda3 for me;

[PHP]dev/disc/disc0/part3[/PHP]

At the sh-3.00# prompt type;

[PHP]grub-install /dev/hda[/PHP]

After being returned to the prompt, do;

[PHP]#umount /dev/hda3
#reboot[/PHP]

Or Ctrl-Alt-Delete will also probably reboot. At this point, how you open the CD drive depends on the machine. Usually if you hit the open button on the drive as the system has just begun to boot (when you see the BIOS name, CPU, and RAM), it will open. If you can't seem to get it open naturally, enter the BIOS setup and change the boot sequence to bypass the CD, boot normally, login, and eject the CD. Try not to use the pin or hard-reset.

You've deleted a partition which alters Ubuntu's hda number - so you may need to [PHP]sudo fdisk -l[/PHP] from a live cd to find the partition number of Ubuntu.

---

