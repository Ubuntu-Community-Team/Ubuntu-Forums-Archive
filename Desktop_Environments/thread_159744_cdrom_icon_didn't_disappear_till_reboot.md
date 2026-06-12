---
title: "cdrom icon didn't disappear till reboot?"
date: 2006-04-13
forum: Desktop Environments
---

### Post by stairwayoflight on 2006-04-13
hi,

i've had a small glitch, reboot seems to have fixed it but i'm trying to figure out what went wrong..

i have 4 ide drives:

/dev/hda - linux
/dev/hdb - ext3 storage disk
/dev/hdc - dvdrom
/dev/hdd - cdrom

both optical drives have mounted audio cds (dvds too for dvdrom) and unmounted okay, but i put a data cd into the cdrom i think, and it wouldn't eject with the eject command, or with the button.

so eject /dev/hdd wouldn't work. then i tried
sudo unmount /dev/hdd and it said 
fstab entries don't agree

because it didn't mount from the beginning i had to do a:
mount /dev/hdd -t auto ~/mountdirectory

to browse the files with nautilus then after i was done it wouldn't eject. the only thing that got rid of it was
umount ~/mountdirectory

can't i pass the device to umount as well?

anyways after that worked i ejected the disk but the icon remained on the desktop, even with 2 other disk icons on for disks in the drives. 'killall nautilus' didn't lose it, i had to reboot.

is this normal???

thanks

---

### Post by Derek Djons on 2006-04-13
Stupid question maybe but do you close the content window of you CD-Rom or DVD-Rom before ejecting.

Yesterday I was installing Diablo II using Wine. The installshield asked me for CD number 2 but I couldn't eject the drive using any command what so ever. After I closed the content window everything worked as it should.

---

### Post by Astrophobos on 2006-04-13
I have a similar problem with blank CD-ROM, DVD-ROM. 

Sometime, after ejecting the media (after burning something to it) the icon stay on the desktop and whatever I do, inserting other blank media or usb flash drive, nothing happen and no more icon are create on the desktop but new entry are create in "Computer" like CD-RW/DVD-R Drive, CD-RW/DVD-R Drive (1), CD-RW/DVD-R Drive (2), ...

---

### Post by stairwayoflight on 2006-04-13
i put in another xp-made data cd (both in explorer, just a file drag and drop operation) and this time it automounted just fine. yah, i closed the file browsing window, the button doesn't eject it but a right click -> eject on the desktop icon ejects it ok.

i'm thinking, because i explicitly mounted the other cd from a terminal (it wouldn't automount) i had to explicity umount it. and correct me if i'm wrong, but "mount/umount 'device'" only works when it can find out what it needs from the fstab? which would explain why i needed the directory for umount to work.

things seem to be working okay now, i'm just wondering why i couldn't get rid of the desktop cd icon till a reboot.

---

