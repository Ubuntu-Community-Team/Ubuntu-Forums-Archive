---
title: "I screwed someting up with my mount point..."
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-03-03
okay, so I have a 4Gb SD Card that I Inserted into my laptop. All went well, it located it, and mounted it, you could see the icon on the desktop. I planned on leaving this card in "permanently" pretty much, just for extra disk space to hold movies. So since I was going to leave it in for long periods of time, I didn't want there to be an icon on the desktop. I figured this is where it was mounting to, so I open up the properties on the SD card and went to "drive". Under that tab, there are "settings" and one of the options is "mount point". What I did was in the field simply typed "/". Now after doing that, it will not let the SD card mount. I get an error saying "unable to mount volume, details: mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)".

How do I get everything back to normal?? I can live with icon on the desktop, please just help me get this fixed!!

---

### Post by gbrainin on 2009-03-03
If you can't change back the properties on the icon, you may need to manually edit your fstab.

---

### Post by sirebral on 2009-03-03
Forcefully mount your flash drive.

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/93082-how-mount-drive.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/93082-how-mount-drive.html)

;)

---

### Post by ChrisMP1 on 2009-03-03
That link opened up to a big long forum page that took me a while to parse, and I'm not exactly a Linux beginner.

Here is how to forcibly mount your drive. Do this just to change the mount point back.

[LIST=1]
[*]Open a terminal (Applications->Accessories->Terminal) to have it ready.
[*]Insert your drive.
[*]Ignoring any errors, at the terminal, type exactly:
```
dmesg | tail
```
[*]Look for a line formatted as: 
```
[000000.000000]   sdb: sdb1
```. You must see 'sd*x***#**, where x is any letter and # is any number. If you don't see this, keep repeating the command, dmesg | tail, until you do.
[*]Enter exactly, replacing sdx# with the code you just found:
```
sudo mount /dev/sdx# /mnt
```
[*]Enter your password and press enter. Nothing will show up.
[*]When you are done with the drive, enter:
```
sudo umount /mnt
```
[/LIST]

---

### Post by Arndtwe on 2009-03-04
> **ChrisMP1 said:**
> That link opened up to a big long forum page that took me a while to parse, and I'm not exactly a Linux beginner.

Here is how to forcibly mount your drive. Do this just to change the mount point back.

[LIST=1]
[*]Open a terminal (Applications->Accessories->Terminal) to have it ready.
[*]Insert your drive.
[*]Ignoring any errors, at the terminal, type exactly:
```
dmesg | tail
```
[*]Look for a line formatted as: 
```
[000000.000000]   sdb: sdb1
```. You must see 'sd*x***#**, where x is any letter and # is any number. If you don't see this, keep repeating the command, dmesg | tail, until you do.
[*]Enter exactly, replacing sdx# with the code you just found:
```
sudo mount /dev/sdx# /mnt
```
[*]Enter your password and press enter. Nothing will show up.
[*]When you are done with the drive, enter:
```
sudo umount /mnt
```
[/LIST]
ok, I tried this, and it did not work :-(. I entered dmesg | tail, and here is the output:```
[  379.065942] mmcblk0: mmc0:b699 SU04G 3979776KiB 
[  379.066076]  mmcblk0: p1
[  449.453838] mmc0: card b699 removed
[  450.319949] mmc0: new SDHC card at address b699
[  450.321341] mmcblk0: mmc0:b699 SU04G 3979776KiB 
[  450.321462]  mmcblk0: p1
[  465.876973] mmc0: card b699 removed
[  467.130545] mmc0: new SDHC card at address b699
[  467.131148] mmcblk0: mmc0:b699 SU04G 3979776KiB 
[  467.131300]  mmcblk0: p1
```

I tried this multiple times with no luck on finding "sdx#"... I even tried the mount command with mmc0 as above, no go. Now, It is obvious though, that the computer "sees" my card, but I can't see it...

---

### Post by sirebral on 2009-03-04
This didn't work?

```
mount -t ntfs-3g /dev/sdb1 /media/disk -o defaults,force,umask=0
```

---

### Post by Arndtwe on 2009-03-05
> **sirebral said:**
> This didn't work?

```
mount -t ntfs-3g /dev/sdb1 /media/disk -o defaults,force,umask=0
```

Nadda. Still can't find any solutions here...

---

### Post by sirebral on 2009-03-05
Even as a Super User?  Thing is, mount is the command you need to use to fix the problem you have.  I think your problem is telling it to mount in a way it understands.  Read up on mount.

---

### Post by Arndtwe on 2009-03-05
Even as super user.Output of given command:>  ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.


Output of /sbin/mount.ntfs-3g --help: > ntfs-3g 1.2216 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2006-2008 Szabolcs Szakacsits
Copyright (C) 2005-2007 Yura Pakhuchiy

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro (read-only mount), force, remove_hiberfile, locale=,
          uid=, gid=, umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

---

### Post by sirebral on 2009-03-05
Well that makes sense.  You need to type ntfs-3g instead of mount.  Try something like the example that is given and report the output here.

---

### Post by Arndtwe on 2009-03-05
Heres the new command I gave "sudo ntfs-3g /dev/sda1 /mnt/win -o force".
Output of that command: > NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by sarang on 2009-03-05
I have had this problem before. The solution that worked for me is outlined below.

run [FONT="Courier New"]gconf-editor[/FONT] and navigate to  [FONT="Fixedsys"]system -> storage -> volumes[/FONT]. You will see some entries under it with names like [FONT="Fixedsys"]_org_freedesktop_Hal_devices_volume_uuid_[/FONT]... 
Click on each one of them and look in the right side pane for the [FONT="Fixedsys"]Name[/FONT]  [FONT="Fixedsys"]mount_point[/FONT]. Right click on that and choose [FONT="Fixedsys"]Unset Key[/FONT]. 

Note that this will not unmount the card - it will only prevent the 'bad mountpoint' error from popping up again.

Removal and re-insert the card, and then it should get mounted at the default mountpoint.

---

### Post by sirebral on 2009-03-05
> **Arndtwe said:**
> Heres the new command I gave "sudo ntfs-3g /dev/sda1 /mnt/win -o force".
Output of that command:

If what sarang says doesn't work you might be attempting to mount your HD and not your Flash Card.  I forget how to find the correct name, but you can find it if it is in.

IOW, make sure you are mounting the correct drive.

---

### Post by Arndtwe on 2009-03-05
> **sarang said:**
> I have had this problem before. The solution that worked for me is outlined below.

run [FONT="Courier New"]gconf-editor[/FONT] and navigate to  [FONT="Fixedsys"]system -> storage -> volumes[/FONT]. You will see at least one entry under it with a name like [FONT="Fixedsys"]_org_freedesktop_Hal_devices_volume_uuid_[/FONT]... 
Click on each one of them and look in the right side pane for the [FONT="Fixedsys"]Name[/FONT]  [FONT="Fixedsys"]mount_point[/FONT]. Right clik on that and choose [FONT="Fixedsys"]Unset Key[/FONT]. 

Note that this will not unmount the card - it will only prevent the 'bad mountpoint' error from popping up again.

Removal and re-insert the card, and then it should get mounted at the default mountpoint.

YESSSSS!!!!!! Thank you so much!! This solved the problem instantly. You are wonderful. Thank thank you thank you

---

### Post by sarang on 2009-03-05
You are very welcome - I am glad it worked.

For future reference, you can set the mount point through the GUI, just do not enter the full path. That is, if you want it to be mounted as /media/foo, just enter foo. I do not know of any way of using the GUI to make it mount at a mountpoint that is not a subdirectory of /media/.

---

### Post by Arndtwe on 2009-03-05
Good to know, thanks again for the info and help. :-D

---

