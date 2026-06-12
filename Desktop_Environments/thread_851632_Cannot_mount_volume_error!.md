---
title: "Cannot mount volume error!"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Questioneer on 2008-07-06
Hello. I get the following popup when plugging in a portable USB drive, or a couple USB sticks.
"Cannot mount volume.
Invalid mount option when attempting to mount the volume."

CDs and DVDs are fine. I've used Hardy before on this computer without this problem before, but I reinstalled it again yesterday.

The problem could lie with the fact that I installed Hardy from a USB drive, But I'm not sure.

Thanks,
Questioneer

---

### Post by Questioneer on 2008-07-06
Using GNOME on ubuntu 8.04, of course. I assume this is a Desktop Environment problem, But I can't tell.
Any help?
thanks,
Questioneer

---

### Post by the_hardy_kid on 2008-07-07
I'm not sure that this will work, as I'm kinda new to Ubuntu 8.04, but, you can mount it manually;

Step 1)
Plug in your usb device

Step 2)
Open terminal (Applications > Accessories > Terminal) and write in
```
 ls /dev/disk/by-label -lah
```

Step 3)
The result should look kinda like this;
```
total 0
drwxr-xr-x 2 root root  60 2008-07-07 15:04 .
drwxr-xr-x 6 root root 120 2008-07-07 15:04 ..
lrwxrwxrwx 1 root root  10 2008-07-07 15:04 \xe7\x9dL3\xea -> ../../sdb1

```

Step 4)
Write this into terminal;
```
pmount /dev/sdb1 USB
```

Note: Change sdb1 in the command in step 4 to whatever comes up on step 3.

E.g, If the result in step 3 was 
```

total 0
drwxr-xr-x 2 root root  60 2008-07-07 15:04 .
drwxr-xr-x 6 root root 120 2008-07-07 15:04 ..
lrwxrwxrwx 1 root root  10 2008-07-07 15:04 \xe7\x9dL3\xea -> ../../sdv7 
```
then put ```
pmount /dev/sdv7 USB
``` into terminal...

---

### Post by sayakb on 2008-07-07
Also try:
```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

---

### Post by Questioneer on 2008-07-07
Hello.
OK. I have no dev/disk/by-label, so I used dev/disk/by-id

Then, I got:
> lrwxrwxrwx 1 root root   9 2008-07-06 19:49 ata-WDC_WD1600JS-75NCB1_WD-WCANM2138805 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 ata-WDC_WD1600JS-75NCB1_WD-WCANM2138805-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 ata-WDC_WD1600JS-75NCB1_WD-WCANM2138805-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 ata-WDC_WD1600JS-75NCB1_WD-WCANM2138805-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-07-06 19:49 scsi-1ATA_WDC_WD1600JS-75NCB1_WD-WCANM2138805 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 scsi-1ATA_WDC_WD1600JS-75NCB1_WD-WCANM2138805-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 scsi-1ATA_WDC_WD1600JS-75NCB1_WD-WCANM2138805-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-07-06 19:49 scsi-1ATA_WDC_WD1600JS-75NCB1_WD-WCANM2138805-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2008-07-06 21:10 usb-Seagate_FreeAgentDesktop_6RY1R4XG-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2008-07-06 21:10 usb-Seagate_FreeAgentDesktop_6RY1R4XG-0:0-part1 -> ../../sdb1

and then I installed pmount, which was not installed.

Then I run pmount /dev/sdb1 USB
> Warning: device /dev/sdb1 is already handled by /etc/fstab, supplied label is ignored
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

THEN I run pmount /dev/sdb USB, and no error is given, but nothing seems to happen!

I would like to possibly fix the problem and be able to have GNOME auto-mount if I can.

Thanks,
Questioneer

---

### Post by Questioneer on 2008-07-07
> 
Also try:
Code:

sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb



Hey! That worked! The drive is now accessible!
Any other drive I put in is also accessible.

Thanks,
Questioneer

---

### Post by vinipl87 on 2008-07-13
Hi Questioneer, I had exactly the same problem of yours.
Recently I installed Ubuntu 8.04.1 image over my 8.04 just for the sake of a clean install - and to test installation through an USB stick. I used UNetbootin, and you?

Well, after that, every time I plugged my USB external drive (ext3) or stick (fat32) I got a "Cannot mount volume." message. I could manually mount them, but Ubuntu automatic mounting was not working..

I noticed strange lines in my fstab file:
> /dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

Due to pendrive install (?) the file system /dev/sdb1, which (on my machine) is normally used by Ubuntu automatic mounting, was pointing to cdrom..

So I removed both lines in fstab and added (to preserve the real cdrom):
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

When I rebooted, everything was working flawlessly as when I installed Ubuntu 8.04 from a live cd!

---

### Post by agitdd99 on 2008-07-21
> **LinuxIsInnovation said:**
> Also try:
```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

hello...i got the same problem too, after experiencing on hardy instalation from an usb stick.

i followed your instructions, and it worked.

many thanks to you, my friends....

---

### Post by Existance0 on 2008-07-22
I am having this problem but it seems to be a bit different,

makedir /media/usb etc...

works but will not let me change any of the files on the usb and if i go to computer it will not show the drive as mounted heres the error i get when tring to delete stuff...

Error removing file: Permission denied

is there a delete command i can use with sudo to maybe try that?

---

### Post by Existance0 on 2008-07-22
bump

---

### Post by registerkar on 2009-10-15
> **sayakb said:**
> Also try:
```
sudo mkdir /media/usb
sudo mount /dev/sdb1 /media/usb
```

Thanks a Lot Dude... I searched the whole net but was not getting the solution for 'Cannot Mount Volume'...U solved my Prob...

Problem: I use live USB Ubuntu 9.04 with Persistent... all of a sudden i was not able to mount 2 of my 1st NTFS partitions of 2 HDDs... Dont know why... 

This Worked:
sudo mkdir /media/Backup
sudo mount /dev/sdb5 /media/Backup
Backup is my Volume Lable for that partition...

Though spaces are not acceptable for volume lable

For my second disk i tried
sudo mkdir /media/Windows XP
sudo mount /dev/sda1 /media/Windows XP

And i got a error...it was not done
so I changed 'Windows XP' to 'WindowsXP' & i was able to mount the volume.

Thanks Again

---

