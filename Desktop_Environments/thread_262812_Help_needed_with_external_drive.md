---
title: "Help needed with external drive"
date: 2006-09-22
forum: Desktop Environments
---

### Post by londonhelper on 2006-09-22
I seem to be having a problem with my external 40gig usb hdd.
I can mount it with sudo mount /dev/sdb1 /media/usbdrive

but its not automounting when u first plug it in, and not mounting at boot either. I can mount it manualy but cant right to it as its mounted as root.

I have tried adding it in the fsstab but still no go. I have tried removing and readding the hal software and autofs etc - still no luck 

the drive is formated vfat - I can read it fine on my other ubuntu box (which actually automounts it too) 
the only difference is that this pc was re-installed yesterday opposed to my machine at home been going a month now ... but this system has been installed from the DVD 6.06.1 So I am not sure how to fix this now.

I would like the drive to automount the vfat 40gig drive so i can write to it as a normal user.

please help
thanks

---

### Post by londonhelper on 2006-09-22
or can anyone tell me how i can mount this normally so i can write to it without being a su
thanks

---

### Post by yeehawjared on 2006-09-22
you want add this in your /etc/fstab 
sudo gedit /etc/fstab


/dev/sdb1       /media/usbdrive     vfat    rw,users,gid=users,umask=000,       0       0

That's an example of a fat32 storage partition I use.  Fat32 is easily read by both linux and windows.  (i know ntfs is possible but it's easier to just have a fat32 partition)

you'll have full permissions to read/write/modify, etc.

hope that helps.

---

