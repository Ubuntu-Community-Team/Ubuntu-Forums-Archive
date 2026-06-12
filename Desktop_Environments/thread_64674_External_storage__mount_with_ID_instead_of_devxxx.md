---
title: "External storage : mount with ID instead of /dev/xxx"
date: 2005-09-11
forum: Desktop Environments
---

### Post by yoloosis on 2005-09-11
Hi everybody !
When we plug an usb external hard-drive, for example, a list of his partitions appears under media:/ in Konqueror. But when we mount a partition, it's mounted under /media/sda1 for example. So, if I first plug an hard-drive and after an usb key, HD will be /dev/sda and the key /dev/sdb. But if I plug the key and after the HD, key will be /dev/sda and the HD /dev/sdb.

I've got my music in a external HD, so when I'm using Amarok (who find my music under /media/sda1), I need to plug my HD first. Isn't possible for Kubuntu to mount external medias under directories with another name, lable for example ?

Imagine my music partition has a label like "MUSIC", Kubuntu will mount it under /media/MUSIC instead of /media/sdX1. It will be great ! A unique mount point...

Perhaps we could use even another descriptor, like device serial number...

Is it possible to do such a thing with Kubuntu ?

Thank you !

---

### Post by cwaldbieser on 2005-09-11
[QUOTE=yoloosis]Hi everybody !
When we plug an usb external hard-drive, for example, a list of his partitions appears under media:/ in Konqueror. But when we mount a partition, it's mounted under /media/sda1 for example. So, if I first plug an hard-drive and after an usb key, HD will be /dev/sda and the key /dev/sdb. But if I plug the key and after the HD, key will be /dev/sda and the HD /dev/sdb.

I've got my music in a external HD, so when I'm using Amarok (who find my music under /media/sda1), I need to plug my HD first. Isn't possible for Kubuntu to mount external medias under directories with another name, lable for example ?

Imagine my music partition has a label like "MUSIC", Kubuntu will mount it under /media/MUSIC instead of /media/sdX1. It will be great ! A unique mount point...

Perhaps we could use even another descriptor, like device serial number...

Is it possible to do such a thing with Kubuntu ?

Thank you ![/QUOTE]
It is actually possible to mount the device anywhere you want if you do it manually or write your own hotplug script.  I am not sure how it works in kubuntu, but in ubuntu, the gnome-volume-manager always mounts devices under /media.

---

### Post by yoloosis on 2005-09-12
Yes, it mount under /media, so it could be /media/sda1 for my first external partition, but I'm guessing if there a way to mount a partition under /media/another_name_than_sda_wy_not_serial_number_or_label_for_example

Thanx for your answer !

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]Is it possible to do such a thing with Kubuntu ?[/QUOTE]

Yes.  Attach both your devices and in a terminal prompt type this:

**sudo blkid**

This will give you the UUID (unique identifier) assigned to your devices.  Edit the /etc/fstab file to add your devices and mount points.

Instead of (example from my /etc/fstab):

/dev/hda1       /               reiserfs notail          0       1

Change it to (whatever the number was):

UUID="34ab8dbd-c7f5-4ca7-b347-c8d2d6b0b594"      /       reiserfs notail          0       1

---

### Post by yoloosis on 2005-09-12
Thank you a lot, it's an excellent hint for what I want to do. So, after a cool RTFM of mount :-), it's said
"Most  devices are indicated by a file name (of a block special device), like /dev/sda1, but there are other possibilities. For example, in  the case  of  an  NFS mount, device may look like knuth.cwi.nl:/dir.  It is possible to indicate a block special device using its volume  label  or UUID (see the -L and -U options below)."

So, I think that the thing who reconize a just plugged device (hal ? hotplug ? udev ?) use the file name (like /dev/sda) by default. Perhaps it is possible to use the UUID or the lable by default... Any idea ?

Really thank you mlomker ! I think it will be a great feature to have an EXPLICIT name and UNIQUE MOUNT POINT BY PARTITION WITHOUT THE NEED TO PLUG DEVICES IN A CERTAIN ORDER under media:/ in konqueror or /media/ in the filesystem.

---

### Post by mlomker on 2005-09-12
[QUOTE=yoloosis]So, I think that the thing who reconize a just plugged device (hal ? hotplug ? udev ?) use the file name (like /dev/sda) by default. Perhaps it is possible to use the UUID or the lable by default... Any idea ?[/QUOTE]

It's a combination of HAL and pmount.  Pmount is what allows the system to mount something that isn't in /etc/fstab.  There must be a script that Ubuntu uses to call pmount and there are some options that could be set.

---

### Post by yoloosis on 2005-09-12
[QUOTE=mlomker]It's a combination of HAL and pmount.  Pmount is what allows the system to mount something that isn't in /etc/fstab.  There must be a script that Ubuntu uses to call pmount and there are some options that could be set.[/QUOTE]
 Ok, I'll take a look to pmount...
Thank you mlomker !

---

### Post by mlomker on 2005-09-13
I looked at this for a while and there isn't any way to totally automate this without manually editing some configuration files.  You can use UUIDs in fstab to mount devices to a consistent location and then chmod the mount point to allow regular users rw access.  Pmount defaults to root-only as rw and it doesn't appear configurable to do what you were wanting to do.

Other distributions (I used Linspire previously) use a different approach that synchronizes fstab rather than using pmount.  Basically the first time that you plug something in a service writes a UUID line into fstab.  It's 'plug and play' as well, but Ubuntu's developers decided that they didn't want fstab rewritten for removable devices.

---

### Post by yoloosis on 2005-09-13
I've got a problem with mount thanks to UUID or Label. Note : I'm using a Debian Unstable at the moment.
When I do a blkid or a mount with UUID or Label, a /etc/blkid.tab is created. But, it is not refreshed avec a reboot... So, if a device is mapped on another point under /dev, it can't be found by mount... So, I have to erase /fstab/blkid.tab before mount with Label... It's a bit useless for the moment ;-) ! Have you an idea ?

---

### Post by mlomker on 2005-09-14
If you delete the file does it get recreated on the next boot?  The command can be called as **blkid -c /dev/null** to prevent the blkid.tab file from being recreated.  The problem is that  I have no idea which startup script would be running it in Debian.

You could try looking through the files in init.d.  This should tell you which files have that command in it:

```

grep -l -e blkid /etc/init.d/*

```

---

### Post by yoloosis on 2005-09-14
An entry is written /etc/blkid.tab each time a filesystem is mounted. So, there is no script with an explicit `blkid` in it. And after a reboot, my blkid.tab seems to be the same as my previous session. So, if devices have changed (HD in /dev/sdb, not /dev/sda for example), I can't mount my partition.

But, and here it's quite fun, if the device is changed WITHOUT rebooting the computer (you know, for example, if I unplug my external HD, plug a USB flash disk and after replug the external HD : HD was /dev/sdb, now it's /dev/sdc), I can mount it thanks to label ! I don't understand why I can't do it just after a boot...

---

### Post by DaBruGo on 2006-03-17
[QUOTE=yoloosis]An entry is written /etc/blkid.tab each time a filesystem is mounted. So, there is no script with an explicit `blkid` in it. And after a reboot, my blkid.tab seems to be the same as my previous session. So, if devices have changed (HD in /dev/sdb, not /dev/sda for example), I can't mount my partition.

But, and here it's quite fun, if the device is changed WITHOUT rebooting the computer (you know, for example, if I unplug my external HD, plug a USB flash disk and after replug the external HD : HD was /dev/sdb, now it's /dev/sdc), I can mount it thanks to label ! I don't understand why I can't do it just after a boot...[/QUOTE]

Hey folks,

Does this mean if I use the "root=UUID" option on the kernel line in GRUB's menu.lst file that it may not work if I reboot or use the drive (external USB unit) on another PC, even if the drive is set as the first boot device?

I have been trying to make this drive truly portable by using either LABEL or UUID options on the kernel line. And currently, the LABEL command doesn't seem to work for me (even with /etc/fstab edited).

Anyone have a good tutorial on using either of these options. I loaded GRUB to the external drive (/dev/sda).

Any thoughts on this?


DAVE

---

### Post by DaBruGo on 2006-03-29
[quote=yoloosis]An entry is written /etc/blkid.tab each time a filesystem is mounted. So, there is no script with an explicit `blkid` in it. And after a reboot, my blkid.tab seems to be the same as my previous session. So, if devices have changed (HD in /dev/sdb, not /dev/sda for example), I can't mount my partition.
 
But, and here it's quite fun, if the device is changed WITHOUT rebooting the computer (you know, for example, if I unplug my external HD, plug a USB flash disk and after replug the external HD : HD was /dev/sdb, now it's /dev/sdc), I can mount it thanks to label ! I don't understand why I can't do it just after a boot...[/quote]
 
yoloosis,
 
 
I don't know if this helps, but I found these commands on a site I was google searching the other night ...
 
ln -s /dev/null /etc/blkid.tab
ln -s /proc/mounts /etc/mtab
 
(I believe you are supposed to delete blkid.tab and mtab after running these link commands.)
 
Evidently, if you set the blkid file that way, it gets re-created every time you start linux (which they said takes a small amount of time at startup). Also the mtab file is set that way because it can get it's info from somewhere else (according to the site). If I don't forget when I get home tonight, I will try to post the URL for the site.
 
Hope that helps.
 
 
DAVE

---

