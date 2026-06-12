---
title: "Partitions ???"
date: 2005-06-23
forum: Desktop Environments
---

### Post by birdman on 2005-06-23
I am new to Linux, but love Ubuntu.
My question is , How can I access my Windows NFTS partition data ???
I may be stupid but I can't find them anywhere, what do I need to do ?

 ](*,)

---

### Post by byen on 2005-06-23
Windows - FAQ - source [www.ubuntuguide.org](www.ubuntuguide.org)

Q: How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows
   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222

   5. To unmount Windows partition

sudo umount /media/windows/

Q: How to mount/unmount Windows partitions (FAT) manually, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows

   4. To mount Windows partition

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o umask=000

   5. To unmount Windows partition

sudo umount /media/windows/

Q: How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only?

   1. Read General Notes
   2. Read How to list partition tables?
   3.e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows

   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?

Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?

   1. Read General Notes
   2. Read How to list partition tables?
   3.e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows

   4.sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  vfat    umask=000       0       0

   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?

_____________________________________________________________________________________________
COPIED FROM [www.ubuntuguide.org](www.ubuntuguide.org)

plase refer to the site for some basic answers to get to started. Hope it helps. Goodluck.

---

### Post by sickdude on 2005-06-24
hey thats what i wanted to copy paste  O:)

---

### Post by afonic on 2005-06-24
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

It's better to just give the link, that copy-paste is difficult to read and it contains links. :-)

---

