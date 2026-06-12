---
title: "Couldn't find &quot;/media/usbdisk&quot;"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Southeast First on 2006-08-22
I apologize if a **working** solution for this has already been posted, but I've scoured the both the forums and google for the past hour and i've yet to find a solution.

I just recently reformated and reinstalled Ubuntu, updated everything, and tryed to plug in my external hd to retrieve my music and pictures when i get the Couldn't find "/media/usbdisk" error.

What was especially peculiar was that I could see the files in on the hd for half a second before getting the error.

What should I do?

---

### Post by Southeast First on 2006-08-22
bump

---

### Post by Lorian on 2006-08-22
I had a similar problem with my CD drives, I found that restarting the computer while leaving the disks in (or in this case, the drive connected), it would let me use it.

---

### Post by Southeast First on 2006-08-22
didn't work...

---

### Post by Southeast First on 2006-08-23
bump

---

### Post by Southeast First on 2006-08-23
> **Southeast First said:**
> bump

](*,)

---

### Post by jackn on 2006-08-23
As it is an external disk, mounted in /media and referred to as 'usbdisk', it must be pmount-hal mounted, like other self-mounted removable devices (hotplugging).
[Please see post # 2.]("http://www.ubuntuforums.org/showthread.php?t=236230")
Indeed, little clear, useful info around. In particular, hotplugging seems to work differently (different filenames, etc) in Ubuntu than in other distros, and don't know where it's explained.

Here's what I'd try.

1. As suggested by Lorian, replugging the device while the box is on, or rebooting with the device plugged in. I do understand you said the latter didn't work.

2. 'locate usbdisk' - to see if it's mounted elsewhere - it has happened to me once that my device was mounted in /tmp for some reason. In case you find other possible mount points, in order to be sure,ls them, to verify by seeing your files. 
If the device is mounted elsewhere, I'd unmount the device (pumount <whatever the device is>) and remove the mount point, and try again (after logging out+in). The device can be found by plugging it in followed by 'dmesg' - the output includes the name of the device.
Alternatively, browse through System>Administation>Discs. Click your disk icon if it's there, and open the 'partitions' tab: 'Access path' should show the familiar /media/... or a new path. When I once tried to correct it from there, it got restored. Finally, somehow the system complied after I removed the bizzare new mount point.

3. Alternative 'solutions' that will allow you to browse and recover your files, but won't be a restoration of the hotplugging:

* To pmount: mkdir /media/usbdisk, then 'pmount <dev/name_from_dmesg_above>'. Should then be under /media/usbdisk.

* To mount - (will overrule pmount-hal procedures) - list device in /etc/fstab. Just copy another line, say that of the floppy, but with the proper device name instead and a new mount point (/media/usbdisk).
You should then be able to mount your device with 'sudo mount /media/usbdisk' and unmount with 'sudo umount /media/usbdisk'. If you do that, you can uncomment it (# at the beginning of the line) to test hotplugging again.

I hate the latter solutions, as hotplugging is, so to speak, so cool, but in spite of a good deal of research, I still don't know where exactly in Ubuntu you would tweak the files to modify or to restore hotplugging.

Hope that helps, and let us know.

Jackn

---

### Post by Southeast First on 2006-08-23
Before i continue...

I went into Disk Manager and it showed up as a "Hard Disk."

Access Path is "none"

---

### Post by jackn on 2006-08-23
> **Southeast First said:**
> Before i continue...

I went into Disk Manager and it showed up as a "Hard Disk."

Access Path is "none"

Know of 'Device Manager' and 'Discs', but not of 'Disk Manager'.

Have you tried replugging again, after a reboot?

Have you studied the references?

What makes you think that 'Hard Disk' is the external USB-hard disk?

What is your device name under /dev?

In order to do something useful, some work and attention to detail are necessary.

Another place to look, which occurs to me now, is Sys>Prefs>Removable Drives and Media.
Under the 'storage' tab, it allows you to decide whether hotplugging should work: The two 'mount' (first two) options under the 'Removal Storage' heading should be checked. 

Jackn

---

### Post by Southeast First on 2006-08-23
sorry, i meant discs
yes i have tried replugging again after a reboot

i know that hard disk is the external because i have one internal that is 200 and an external that is 160. that shows as being 160

it shows up as /dev/sda but sometimes as sda1

i apologize about the lack of details.

in the "disk manager" (what i get after going to "disks") in the partitions tab it shows "Partition 1" having the following attributes:

Device: /dev/sda
Filesystem: unformatted
Access Path: none
Size: 149.05GB (free space not available)
Status: innaccessable

and both tabs are checked in removable media's "storage" tab

---

### Post by Southeast First on 2006-08-23
Also, now it stays on the desktop as usbdisk but when I try to browse it gives me a 

"The folder contents could not be displayed.

Sorry, couldn't display all the contents of 'usbdisk'." error.

And in the Disks partition tab it tells me:

Device: /dev/sda1
Filesystem: Windows NFTS
Access Path: /media/usbdisk
Size: 149.05GB (96.17GB free)
Status: Accessbile

---

### Post by jackn on 2006-08-24
OK, now there's some detail and it's clear, have been barking up the wrong tree, as this is clearly *not* a mounting problem. 

To verify:
```
mount | grep usbdisk 
```
should output a line about your device.

The issue is:
'The folder contents could not be displayed.
Sorry, couldn't display all the contents of 'usbdisk'." error.'

If it were a permissions issue, it would say so, but you can check by running:

```
ls -l /media/usbdisk
```

It should show whether you're allowed to read your disk.

The r's at the beginning of the following ouput, for example, show that all can read the partition:

```
drwxr-xr-x 13 root root 32768 Jan  1  1970 /media/hda1
```


More practically, Sys>Admin>Discs, the 'Disk Manager' window you refer to, may be of help. 
Where it says 'inaccessible', it should be possible to widen the window by dragging the righthand border (the pointer changes to an arrow and border icon). This may reveal 'enable' and 'browse' buttons. 
On my system, I can toggle between 'accessible' and 'inaccessible' with the 'enable' (or 'disable') button.

Jackn

---

### Post by Southeast First on 2006-08-24
alright. so, i am not sure exactly what's going on anymore. i started messing around with crap and didn't record anything i did, like a moron, so i look further for some help. i was talking to someone over AIM and he started to go through.

this is what we did:

sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222

and got

mount: /dev/sdb1 already mounted or /media/sdb1 busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/sdb1

then

sudo umount /dev/sdb1

and got

umount: /media/usbdisk-1: device is busy
umount: /media/usbdisk-1: device is busy

now when I got to the disks manager, the /dev/sbd1 registeres as being windows ntfs, access path /media/usbdisk-1, size shows fine, and is accessible but when i try to browse it takes me to my home folder.

so i ejected the disk and it ejected fine, and then /tmp/disks-conf-sdb1 shows up on my desktop

then i unplugged it and re-plugged it in.

and /tmp/disks-conf-sdb1 dissappeared, usbdisk-1 came back, opened in file browser, and it loaded everything that was supposed to be on the disk. 

then I tried to transfer some files to /home/matt/My Music/ and it asked if i wanted to skip or overwrite, etc. so i chose skip then it just went right back to the home folder.

now i'm getting an "The folder contents could not be displayed." "Sorry, couldn't display all the contents of "usbdisk-1"." error and only about 1/6 of the contents show up.

as everything stands right now, in my disks "disks manager" i have three Hard Disks listed, 

one is my hdd
one is /dev/sdb1, filesystem: windows ntfs, access path: /media/usbdisk-1, size matches the external harddrive, and access: accessbile
the last is /dev/sdc1, filesystem: unknown, access path: /media/usbdisk, (Free space not available), and access: inaccessbile

---

### Post by Southeast First on 2006-08-24
anyone?

---

### Post by Southeast First on 2006-08-24
sigh

---

### Post by Southeast First on 2006-08-25
](*,)

---

### Post by Southeast First on 2006-08-25
...

---

### Post by Southeast First on 2006-08-30
:confused:

---

### Post by Southeast First on 2006-09-02
anyone?

---

