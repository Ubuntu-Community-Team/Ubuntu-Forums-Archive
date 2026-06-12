---
title: "Rename A USB Drive"
date: 2008-12-10
forum: General Help
---

### Post by CarlosinFL on 2008-12-10
Every time I plug in my USB external drive to any Linux machine including my 8.10 desktop, the name is in full CAPS.

```
cwilliams@tunafish:~$ mount
/dev/sde1 on /media/BLACKBOOK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
```

Is there a way in command line only to change the name w/o losing on of the data? Obviously I am going to back the data up 1st before I try anything but I would like to avoid losing anything and changing the name for the mount to be all lower case 'blackbook'.

---

### Post by stoneage on 2008-12-10
I think this is it - [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by CarlosinFL on 2008-12-12
> **stoneage said:**
> I think this is it - [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

I don't understand. I am following the commands and when I do - it renames my drive however its in all CAPS. I don't understand why since I typed the new label name in lower case but it still does it in all CAPS.

Here is exactly what I did per the instructions...

```
cwilliams@tunafish:~$ sudo mlabel -i /dev/sde -s ::
[sudo] password for cwilliams: 
Total number of sectors (503775) not a multiple of sectors per track (63)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test
cwilliams@tunafish:~$ echo mtools_skip_check=1 >> ~/.mtoolsrc
cwilliams@tunafish:~$ sudo mlabel -i /dev/sde ::dell_usb

```

Then I see the following:

```
/dev/sde on /media/DELL_USB type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

What am I doing wrong? I want 'dell_usb' not 'DELL_USB' :confused:

---

### Post by robzy on 2008-12-12
> **Carlwill said:**
> What am I doing wrong? I want 'dell_usb' not 'DELL_USB' :confused:

Not sure if this helps much, but I have found some quirkiness when it comes to USB Drive's names.

In Windows Vista (the OS I'm in now) whatever I set it to it comes out as all-caps.

Rob.

---

### Post by Slim Odds on 2008-12-12
A disc label and a mount point are two different things.

Here are you finding the DELL_USB mount point info?

---

### Post by omegamike3 on 2008-12-12
If I remember correctly, the disk label for a FAT32 partition will always be in caps due to the limitations of the file system itself...

---

### Post by CarlosinFL on 2008-12-12
> **omegamike3 said:**
> If I remember correctly, the disk label for a FAT32 partition will always be in caps due to the limitations of the file system itself...

That makes sense...

Thanks all!

---

### Post by CarlosinFL on 2008-12-12
> **omegamike3 said:**
> If I remember correctly, the disk label for a FAT32 partition will always be in caps due to the limitations of the file system itself...

Hmmm - It appears this is not the case...

---

### Post by HermanAB on 2008-12-12
Install the "mtools" package. This package supplies the "mlabel" program. Add the following line to
/etc/mtools.conf:
drive p: file="/dev/sdb1". 

The p: device name is arbitrary. The default config will cover your floppy drives, but adding such a line will probably be needed to assign a dos type device name to a linux device. The /etc/mtools.conf file is well commented with plenty of commented out examples.

Use the appropriate value for the device, either /dev/sda1 or /dev/sdb1 in your case.  You can see what is what with:
$ dmesg

or
$ ls /dev/sd*

Now you can use mlabel to relabel the drive like this:
mlabel p:label 

---

You should also add mtools_skip_check=1 to /root/.mtoolsrc to handle flash disks with strange sector sizes.

---

If a volume has no label, then it gets mounted as /media/disk
If a volume has a label, then it gets mounted as /media/LABEL
(DOS labels are always uppercase.)

If a second device is plugged in with the same volume label, then it gets mounted as /media/LABEL-1
or if no label as /media/disk-1

At power-up, multiple drives with the same label are numbered arbitrarily.

Cheers,

Herman

---

