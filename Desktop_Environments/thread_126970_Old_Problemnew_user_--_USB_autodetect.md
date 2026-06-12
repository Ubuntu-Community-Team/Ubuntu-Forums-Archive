---
title: "Old Problem/new user -- USB autodetect"
date: 2006-02-07
forum: Desktop Environments
---

### Post by wpp42000 on 2006-02-07
I am a new Kubuntu user.  Just installed BreezyBadger on a standard x86 box.  No problems.  Then I inserted a Lexar Thumbdrive that has files written on a Windows box.  Got a Konqueror error:  An error occurred while loading media:/sda1 (later got it to say media:/sdb1) - file or folder does not exist.

If I go to a terminal window and type "sudo fdisk -l', I get:
/dev/sdb1 *   W95 FAT32, then
cd /media and I show a MY_FLOPPY directory (MY_FLOPPY is the volume name of my thumdrive).  If I cd to MY_FLOPPY and do a dir, all of my files show up.  

So what do I need to do to make Konqueror see my thumbdrive correctly?   Is this an install problem or what...?

---

### Post by wpp42000 on 2006-02-08
I found some related posts on iPod problems and a blog that gave me a clue.  Here is what I did to make my USB thumbdrive work as a "sneaker net" between Windows and Kubuntu Linux.

1.  Insert the thumbdrive.  Konqueror shows an error...ignore this.
2.  > dmesg
     get the device name from the log (mine was sda)
3.  > cd /media
4.  > sudo mkdir sda  (the name from #2 above)
5.  > sudo nano /etc/fstab
   add the line:
  /dev/sda1   /media/sda   vfat  user,noauto,umask=000 0 0
  ^O  (write the file)
  ^x  (exit nano)
6.  sudo mount /dev/sda1    (this will fail, so I don't know if it is needed)
7.  Insert the thumbdrive.  Konqueror should show the directory contents.  
8.  > sudo reboot
9.  Repeat step 7 to be sure the changes are permanent.

P.S.  I think this should be part of the standard install for Kubuntu.

---

