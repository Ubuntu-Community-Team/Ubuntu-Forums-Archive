---
title: "Backup root partition and restore"
date: 2009-02-22
forum: General Help
---

### Post by itlarson on 2009-02-22
I need a good way to recover if some things I am doing to my mythbuntu system break it.  My idea is to back up my root directory to a usb flash drive, and then restore it if things go wrong. Would something like this work?

-to back up:
dd if=/dev/sda1 of=/dev/sdb bs=4k  (or of=/dev/sdb1 ?)

-to restore:
dd if=/dev/sdb1 of=/dev/sda1 bs=4k  (or if=/dev/sdb ?)

sda1 is my root directory, and sdb would be the flash drive.
I assume I would boot from a rescue disk to restore, but would I have to do this when making the backup, so the partition wouldn't be active?  Also what does the bs=4k do? I just borrowed this code from a post in the forums, and don't fully understand how it works.

---

### Post by DagMan on 2009-02-23
As I understand it, you'de want to use dd with your hard drives unmounted so using a live cd or liveusb would be ideal.  You'lle find that a live cd will have your swap partition mounted, to turn that off, fire up the partition editor and right click on it, select swapoff or unmount or whatever the option is labeled.

Also you have an error in the commands as posted, as addressed in the questions in your comments.  If you want to back up the entire thing including the MBR... the entire disk, partitions, etc, you'de just use if=/dev/sda but if you only wanted to back up one partition without anything else... no MBR which you would want to boot, then you'de use the partition number if=/dev/sda1 or if=/dev/sda2 or whatever the partition you wanted.  As far as where the output file goes, of=/dev/sdb would be fine, and to restore you'de go dd if=/dev/sdb of=/dev/sda assuming you did the entire disks... but it's also good to know that you can just as easily store it to a file, so to back up the entire disk (as an example) from a live cd and with /dev/sdb1 mounted at /mnt **in the live cd ram environment** (and remember you still want /dev/sda unmounted), you could just as easily do dd if=/dev/sda of=/mnt/my-backup-image and then it would be a file on your external drive.

It's important to note that dd copies every single bit on your hard drive, so whatever you backup to needs to be as big or bigger than the drive youre backing up.  You can filter it through gzip to compress the data, but thats getting ahead of things.

Another utility that I've heard good things about is partimage, though I haven't used it.

Another way to backup your system, and using compression while NOT copying every bit of unused free space like dd does is outlined in this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)  I've used this a number of times.

Recently, I've found that the easiest way to do it, and do it using a USB stick, is to install the program remastersys.  It will make a compressed image file of your current install that can be burned to CD DVD or that can be used to make a liveusb install disk.  You'lle want to exclude your home folder and back it up separately if you have enough on it.  An image file can only be so big before it doesn't fit on anything.  You'lle want to google for remastersys so you can add the repository that hosts the program if you go this route, and while you're at the webpage, read the instructions there as they are easier to understand than the man page.

---

### Post by speed32219 on 2009-04-13
DagMan, thanks for the information.  As I understand it, if I have two 500GB HD's installed, according to what you posted I should be able to unmount them after booting from a live cd and use dd to basically mirror the first drive with all the partitions, data, etc.  I am building another PC that has the exact same HW and instead of installing everything from scratch including my special programs, I can make an exact copy of my current drive.

I was thinking of using fake raid 0 or ubuntu's mdadm raid 0 to do this, but maybe the DD is the way to go.  Any suggestions?

---

