---
title: "External USB HD Woes"
date: 2009-03-01
forum: General Help
---

### Post by cyberia81 on 2009-03-01
Hello. I would greatly appreciate it if someone out there could walk me through how to fix this problem.

I have a 500 GB Western Digital external usb hard drive. I was using it as a back up drive. It was working with Ubuntu flawlessly for months. I recently had to help my fiance reinstall XP and Ubuntu. He backed up his data from his XP partition onto my external hd. Now I can't access my data. Ubuntu doesn't seem to recognize the drive exists. I've tried it on my computer and his. I've also tried it with XP and Vista. They don't recognize the drive.

Here is the output of lsusb:

```
stephanie@boxofmallards:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Here is the output of fdisk -l:

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068173

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30233   242846541   83  Linux
/dev/sda2           30234       30515     2265165    5  Extended
/dev/sda5           30234       30515     2265133+  82  Linux swap / Solaris

```

I've looked around but haven't found anything relevant. Please tell me there is something I can do to get this working again! Thank you for your time.

---

### Post by chriskin on 2009-03-01
i do not know what the problem might be, i just thought that i might have to tell you that one or two months ago my **western digital 500gb usb external drive **showed the exact same problem.

i used a program to recover some of the files but there where many files that were recovered just partially or failed to recover, and i eventually had to reformat it in order to make my systems recognise it

hope you find a better solution :)

---

### Post by cyberia81 on 2009-03-01
I really hope that isn't how things turn out! Did you use WD's software or something else? I'm curious to know but wary of trying it if it didn't do a good job of recovering data... Thanks for the info!

---

### Post by chriskin on 2009-03-01
i had some problem trying to remember the name of the software, that's why i did not mention the name

it was not wd's though, it was a windows application my brother found

---

### Post by cyberia81 on 2009-03-01
Another bit of info that might be pertinent:

I recently (a few weeks before this problem occurred) removed a CD/DVD RW drive from my computer. It is still out. I currently have one DVD installed, an internal hd, and the floppy drive. 

When I look in /media I have the following listed:

cdrom
cdrom0
cdrom1
floppy
floppy0

Could this be related at all? Is there a way to "refresh" these entries?

Thanks!

---

### Post by mulligan.can on 2009-03-01
What filesystem was/is the drive formatted to? When you say that he backed up his data onto it HOW exactly did he do this? Just copy the files over or mirror the partition?

Just confirming, that is the output of lsusb when the drive is plugged in correct?

Can you unplug the drive, wait a minute and then plug it in again and post the output of:

dmesg|tail

please?

---

### Post by cyberia81 on 2009-03-01
The drive was/is formatted with NTFS.

That is the output of lsusb with the drive plugged in.

Dmesg | tail:

```
[ 7425.869300] scsi 3:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9321 PQ: 0 ANSI: 0
[ 7425.871080] scsi 3:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9321 PQ: 0 ANSI: 0
[ 7425.933122] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 7425.933772] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 7425.945153] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[ 7425.945822] sd 3:0:0:1: Attached scsi generic sg3 type 0
[ 7425.951176] sd 3:0:0:2: [sdd] Attached SCSI removable disk
[ 7425.951935] sd 3:0:0:2: Attached scsi generic sg4 type 0
[ 7425.954984] sd 3:0:0:3: [sde] Attached SCSI removable disk
[ 7425.955631] sd 3:0:0:3: Attached scsi generic sg5 type 0

```

Thanks!

---

### Post by mulligan.can on 2009-03-01
Woah... I'm pretty sure I'm not seeing things... Have you got 4 external drives plugged in?

Anyway, ubuntu seems to be recognising the drive[s] which is a good thing, not a hardware failure.

Try typing in "sudo fdisk -l"
That will give you a read out of all the partitions on all the disks attached to the pc.

---

### Post by cyberia81 on 2009-03-01
Oops, sorry. Grabbed the USB card reader and plugged that in. This is the output when my hd is plugged in:

```
[ 9054.180083] usb 3-1: device descriptor read/64, error -71
[ 9054.404032] usb 3-1: device descriptor read/64, error -71
[ 9054.620044] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 9054.740118] usb 3-1: device descriptor read/64, error -71
[ 9054.964047] usb 3-1: device descriptor read/64, error -71
[ 9055.180146] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 9055.588040] usb 3-1: device not accepting address 4, error -71
[ 9055.700061] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 9056.116024] usb 3-1: device not accepting address 5, error -71
[ 9056.117323] hub 3-0:1.0: unable to enumerate USB device on port 1

```

I have **no** idea what that is all about. It doesn't look good though. :confused:

sudo fdisk -l gives the same output as before.

Thank you very much for your help so far!!

---

### Post by mulligan.can on 2009-03-01
> **cyberia81 said:**
> Oops, sorry. Grabbed the USB card reader and plugged that in. This is the output when my hd is plugged in:

```
[ 9054.180083] usb 3-1: device descriptor read/64, error -71
[ 9054.404032] usb 3-1: device descriptor read/64, error -71
[ 9054.620044] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 9054.740118] usb 3-1: device descriptor read/64, error -71
[ 9054.964047] usb 3-1: device descriptor read/64, error -71
[ 9055.180146] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 9055.588040] usb 3-1: device not accepting address 4, error -71
[ 9055.700061] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 9056.116024] usb 3-1: device not accepting address 5, error -71
[ 9056.117323] hub 3-0:1.0: unable to enumerate USB device on port 1

```

I have **no** idea what that is all about. It doesn't look good though. :confused:

sudo fdisk -l gives the same output as before.

Thank you very much for your help so far!!

Haha, I thought that may have been the case. Yeah that doesn't look good. My brand new drive was doing the exact same thing a couple of days ago. It also sported a corrupted filesystem which may have had a bearing.

Ok, that readout explains why fdisk isnt reporting anything. The system isn't even able to connect to the device.

I managed to get mine to connect by unplugging the drive from the usb port and then turning the drive off (it has its own power supply) and waiting a few minutes before connecting it up again.

That let the system at least enumerate the drive so that I could work on it. Pretty sure it was all just a fluke though.

Perhaps try plugging it into a different usb port? Sorry, I'm just not familiar with this sort of thing once it gets to the point where the device won't even connect.

Haha, I'm prolly gonna get shot down for this but... Have you tried connecting it to a windows xp machine and opening disk management? (right click on "my computer" and hit "manage" and then open the "storage" bit)

---

### Post by cyberia81 on 2009-03-01
Well, I certainly appreciate your help! Thanks for everything. I just tried plugging it into my laptop running Slax Live and it gives the same type of dmesg output about "device descriptor read/64, error -71." 

I hope that someone knows how to get around this so that I can get my data back. If it's toast I understand, but I'd really like to retrieve what I can if possible. 

I did try using XP and Vista, thinking that maybe my fiance didn't shut it down properly by chance. Neither OS can even see the drive.

:(

---

### Post by mulligan.can on 2009-03-01
Even when using the disk management console in windows? That really doesn't sound good. If neither OS can detect even the disc forgetting partitions then it could be a hardware fault.

---

### Post by cyberia81 on 2009-03-04
Update - I bought a SATA to USB adapter. Now the drive is visible, but when I try to open it I get the message "Unable to mount location." Any ideas?

---

### Post by wankel on 2009-05-30
I wanted to suggest to take the drive out of the external box and connect it internally to the computer 

Now I'm confused: 

> have a 500 GB Western Digital external usb hard drive.

> Update - I bought a SATA to USB adapter. 

Do you mean that you've got an adapter to make a USB-disk connect to SATA? Or did you swap the old external box with the adapter?

Still the same, have you tried taking the disk out of the enclosure and connect it as such to a pc? It takes away some levels of translating error codes on their way from the disk to the OS (whether it be Linux or Windows)

Good luck

---

### Post by aarons6 on 2009-05-30
> **cyberia81 said:**
> Update - I bought a SATA to USB adapter. Now the drive is visible, but when I try to open it I get the message "Unable to mount location." Any ideas?


most likely what this means is your drive letter changed and you dont have a folder in the /mnt tree to auto mount it to..

---

