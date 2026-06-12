---
title: "ipod automount broke - what can I do?"
date: 2006-01-01
forum: Desktop Environments
---

### Post by linuxted on 2006-01-01
I'm stumped.  

I had to rebuild Ubuntu Breezy (long story) and I can no longer get my ipod nano to automount.   The ipod used to say "please don't disconnect" or something to that effect when I connected it to my USB port.  Now I get no indication that it knows it is connected to a computer other than the screen lighting up.  


This used to work great before I rebuilt the system.

here is what dmesg | tail says:

[4294720.736000] Bluetooth: RFCOMM ver 1.5
[4294720.736000] Bluetooth: RFCOMM socket layer initialized
[4294720.736000] Bluetooth: RFCOMM TTY layer initialized
[4294721.359000] eth0: no IPv6 routers present
[4294764.255000] usb 4-6: new high speed USB device using ehci_hcd and address 3r

I have no idea why bluetooth is initialized... but that is another discussion.

here is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /mnt/backup     ext3    noauto,users    0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


I don't recall doing anything special last time I go the ipod to work on Breezy, so I'm hesitant to try some of the things I see on the forums.

I have gnome-volume-manager running.  I'm lost!:confused: 

please help

thanks

---

### Post by linuxted on 2006-01-01
[QUOTE=linuxted]I'm stumped.  

I had to rebuild Ubuntu Breezy (long story) and I can no longer get my ipod nano to automount.   The ipod used to say "please don't disconnect" or something to that effect when I connected it to my USB port.  Now I get no indication that it knows it is connected to a computer other than the screen lighting up.  


This used to work great before I rebuilt the system.

here is what dmesg | tail says:

[4294720.736000] Bluetooth: RFCOMM ver 1.5
[4294720.736000] Bluetooth: RFCOMM socket layer initialized
[4294720.736000] Bluetooth: RFCOMM TTY layer initialized
[4294721.359000] eth0: no IPv6 routers present
[4294764.255000] usb 4-6: new high speed USB device using ehci_hcd and address 3r

I have no idea why bluetooth is initialized... but that is another discussion.

here is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /mnt/backup     ext3    noauto,users    0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


I don't recall doing anything special last time I go the ipod to work on Breezy, so I'm hesitant to try some of the things I see on the forums.

I have gnome-volume-manager running.  I'm lost!:confused: 

please help

thanks[/QUOTE]


More info, all of it bad....   printer (usb connected) is acting up.   Sometimes it prints, sometimes it doesn't.

USB flash drive sometimes is recognized, most often it is not:
dmesg gives
[4298531.739000] sdb : READ CAPACITY failed.
[4298531.739000] sdb : status=0, message=00, host=7, driver=00
[4298531.739000] sdb : sense not available.
[4298531.799000] sdb: Write Protect is off
[4298531.799000] sdb: Mode Sense: 00 00 00 00
[4298531.799000] sdb: assuming drive cache: write through
[4298531.949000] sdb : READ CAPACITY failed.
[4298531.949000] sdb : status=0, message=00, host=7, driver=00
[4298531.949000] sdb : sense not available.
[4298531.979000] sdb: Write Protect is off
[4298531.979000] sdb: Mode Sense: 00 00 00 00
[4298531.979000] sdb: assuming drive cache: write through
[4298531.979000]  /dev/scsi/host2/bus0/target0/lun1: unable to read partition table


lsusb command usually hangs with no output

I tried reinstalling gnome-volume-manager, rebooting, saying a quick prayer :) ... no luck.   


any ideas?  I'm going nuts

Thanks

---

### Post by linuxted on 2006-01-01
[QUOTE=linuxted]More info, all of it bad....   printer (usb connected) is acting up.   Sometimes it prints, sometimes it doesn't.

USB flash drive sometimes is recognized, most often it is not:
dmesg gives
[4298531.739000] sdb : READ CAPACITY failed.
[4298531.739000] sdb : status=0, message=00, host=7, driver=00
[4298531.739000] sdb : sense not available.
[4298531.799000] sdb: Write Protect is off
[4298531.799000] sdb: Mode Sense: 00 00 00 00
[4298531.799000] sdb: assuming drive cache: write through
[4298531.949000] sdb : READ CAPACITY failed.
[4298531.949000] sdb : status=0, message=00, host=7, driver=00
[4298531.949000] sdb : sense not available.
[4298531.979000] sdb: Write Protect is off
[4298531.979000] sdb: Mode Sense: 00 00 00 00
[4298531.979000] sdb: assuming drive cache: write through
[4298531.979000]  /dev/scsi/host2/bus0/target0/lun1: unable to read partition table


lsusb command usually hangs with no output

I tried reinstalling gnome-volume-manager, rebooting, saying a quick prayer :) ... no luck.   


any ideas?  I'm going nuts

Thanks[/QUOTE]


Ok, I bit the bullet and rebuilt my system.  This time before I did the kernel update I tried connecting.  usb printer works, usb memory stick works and ipod is charging when connected.

With the ipod connected and doing a dmesg I get:
usb 4-7: new high speed USB device using ehci_hcd and address 6


lsusb hangs again :(

what the heck is going on???


here is my /etc/fstab just in case
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0
   1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


Your help is much appreciated!

---

### Post by linuxted on 2006-01-02
I installed a utility called "ipod" to scan for anything connected to the USB port.

#ipod
Listening for iPod-specific HAL events...

and it just sits there.

I don't think the computer has a clue that the ipod is connected, yet all other usb devices seem to be working.

I'm so frustrated

thanks for listening

---

### Post by astoltz on 2006-01-02
Maybe it's a problem with the ipod itself?  Is there another machine you can try it on?

---

### Post by linuxted on 2006-01-02
[QUOTE=astoltz]Maybe it's a problem with the ipod itself?  Is there another machine you can try it on?[/QUOTE]

I have a windows machine that I'm reluctant to try this on but I may have to.

However this ipod worked a week ago with Breezy and I have another ipod nano that is behaving identically.

I appreciate the post, thank you for asking

---

### Post by linuxted on 2006-01-02
[QUOTE=astoltz]Maybe it's a problem with the ipod itself?  Is there another machine you can try it on?[/QUOTE]


Just to be complete, I connected the ipod to the windows machine and it connects no problem.

I also restored the software on the ipod using the included disk (which wiped out all my songs (I have several backups).

I reconnected to Linux ... no luck.  In fact, the screen doesn't even light up now

---

### Post by RoninGurl on 2006-01-02
I had a similar problem with my iPod  (3rd generation) in the firewire port. Despite unmounting the iPod in Gnome and safely dismounting the volume for some reason Ubuntu would not change the "Do not Disconnect" to the check mark where you can safely disconnect. And after several more attempts I just decided to disconnect the iPod since I hadn't added or removed any songs from it so I figured it was safe. 

Eh, it wasn't. The iPod refused to turn on and show its navigation menu, but i was still hearing the navigation scrolling click. So I opened up the iPod manual and found the reset key combination and forced a hard reboot in the iPod firmware so that I could use it again on and off the computer. Though I never had to reinstall the firmware. And luckily I did not loss any music (even though I had backups). 

But since it works in Windows for you and just not Ubuntu then I'm going to have to say that you have some sort of conflict going on there. Have you tried switching USB ports?

---

### Post by linuxted on 2006-01-02
[QUOTE=RoninGurl]I had a similar problem with my iPod  (3rd generation) in the firewire port. Despite unmounting the iPod in Gnome and safely dismounting the volume for some reason Ubuntu would not change the "Do not Disconnect" to the check mark where you can safely disconnect. And after several more attempts I just decided to disconnect the iPod since I hadn't added or removed any songs from it so I figured it was safe. 

Eh, it wasn't. The iPod refused to turn on and show its navigation menu, but i was still hearing the navigation scrolling click. So I opened up the iPod manual and found the reset key combination and forced a hard reboot in the iPod firmware so that I could use it again on and off the computer. Though I never had to reinstall the firmware. And luckily I did not loss any music (even though I had backups). 

But since it works in Windows for you and just not Ubuntu then I'm going to have to say that you have some sort of conflict going on there. Have you tried switching USB ports?[/QUOTE]

Yes I have tried switching USB ports with no luck.  I have had to reset the ipod before when it locked up, but that was a different situation.  Resetting it now doesn't seem to help.

After doing alot of reading in here and seeing how many are suddenly having mp3 player automount problems, I think there is a kernel bug with USB2.0 and automounting.

---

### Post by linuxted on 2006-01-07
After interaction with the folks at Bugzilla, it turns out USB2.0 is having problems.  Not sure if it is Breezy or the kernel, but it is a known problem that is (hopefully) being worked.

---

### Post by linuxted on 2006-01-19
With the latest kernel update (2.6.12-10-amd64-generic) things are all better now (and its USB2.0)

---

### Post by linuxted on 2006-04-13
Crud... it broke again and I have been unsuccessfull in fixing it.  Did something change in the kernel again? 

:confused: ](*,)

---

