---
title: "Help formatting and writing to external usb drive"
date: 2006-04-26
forum: Desktop Environments
---

### Post by BoboChimp on 2006-04-26
I was just given a hard drive that i would like to use as an external drive.  i managed to repartition it on an XP box i have.  I couldn't figure out how to over ride the "read only" settings in Ubuntu.  I brought it back to my Ubuntu machine to format vfat (xp only formats ntfs apparently).  

I'm pretty sure i managed to get the FS on correctly b/c it shows as vfat in Disks Manager.  The problem is that Root is the owner.  I cannot write to the disk as a regular user.  You'd think if you format a disk from inside a user account (albeit, i did have to use my sudo password to access Disks Manager), you would be the owner of it.

I followed the advice in this thread:
[http://www.ubuntuforums.org/showthread.php?t=122523](http://www.ubuntuforums.org/showthread.php?t=122523)

but i must have done something wrong b/c it still shows root as the owner.  

Can anyone help out?

---

### Post by Ramses de Norre on 2006-04-26
How did you mount it? FAT doesn't support user permissions so the permissions you see are caused by fstab only.

Mount it like this:```
/dev/hda1       /mnt/hda1  vfat iocharset=utf8,umask=0000 0 0

``` with /dev/hda1 the device node (will be /dev/sdxx with an external usb, fill in the correct values for xx, you can find them with sudo fdisk -l) and /mnt/hda1 the mount point.

---

### Post by BoboChimp on 2006-04-26
Ramses,

I'm sorry man.  I wish I had more experience with linux to understand fully what you are saying.  Could you elaborate a little more?  

I didn't mount it and maybe that is the problem.  it is plugged into the usb port and i can see it on the desktop.  i just can't move files to it.

what would the command line entry be to mount it?

edit...

all right, i followed the wiki and did something to this effect...
      
  sudo mkdir /backup
     
  sudo mount /dev/sdb1 /backup

now i just can't figure out how to access it

---

