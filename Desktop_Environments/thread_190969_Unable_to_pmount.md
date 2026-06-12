---
title: "Unable to pmount?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by alvinblank on 2006-06-06
I've a few partition in Places -> Computer that I thought would be better to access than mounting the same partition using fstab. When try to access it gives the error. If it can't be access why does Ubuntu auto-magically add them. 
[[IMG]http://img424.imageshack.us/img424/6635/screenshot6ti.th.png[/IMG]](http://img424.imageshack.us/my.php?image=screenshot6ti.png)

---

### Post by Ramses on 2006-06-07
Check that you have pmount installed.

---

### Post by playmobiel on 2006-06-08
I have also the same problem , pmount is installed

---

### Post by HyperY2K on 2006-06-15
I've got the same problem, but with an Debian and Gnome 2.14 it works for me. Strange, or?

---

### Post by HyperY2K on 2006-06-17
UPDATE
I've updated my Debian now, too (it's testing ;-) ) and with my Laptop running Debian testing pmount works and on my workstation (Debian testing and Ubuntu 6.06) both say pmount don't work, because the device is not a removable device. 
I think it's a general pmount error or?

---

### Post by asearle on 2006-06-19
I think I have the same problem:  I have installed Ubuntu and the system found my existing drives (one NTFS and one FAT32) and even included my Windows boot in GRUB (that works fine) but when I try to access the drives (from Computer / File browser) I get the following message:

Unable to mount the selected volume
error: device /dev/hda1 is not removable
error: could not execute pmount

I checked my system and see that pmount is installed.

Does anyone have any tips for me?  Is there a problem?  Or have I simply omitted to do something?

Many thanks for your help.

Regards,
Alan Searle

---

### Post by HyperY2K on 2006-06-19
anybody a solution?

---

### Post by HyperY2K on 2006-06-21
i've got the solution:
just add a line in /etc/pmount.allow, like
/dev/hda1

---

### Post by mardok on 2006-06-21
[QUOTE=HyperY2K]i've got the solution:
just add a line in /etc/pmount.allow, like
/dev/hda1[/QUOTE]


i've tryed to do this but this isn't a solution for me.

but when i try this command
sudo mount  /dev/sda1 /mnt
the mount command work correctly

---

### Post by HyperY2K on 2006-06-21
which error message do you get from pmount?

---

### Post by mardok on 2006-06-21
[QUOTE=HyperY2K]which error message do you get from pmount?[/QUOTE]

The error message isn't changed

"error: device /dev/sda1 is not removable

error: could not execute pmount"

i think this happens because the value in /sys/block/sda/removable is set to 0
but i can't change this value because it is an only read file

---

### Post by HyperY2K on 2006-06-21
did you add /dev/sda1 to pmount.allow ?

---

### Post by mardok on 2006-06-21
[QUOTE=HyperY2K]did you add /dev/sda1 to pmount.allow ?[/QUOTE]


this is my pmount.allow file:

/dev/sda5 umask=0555
/dev/sda1 umask=0555

---

### Post by HyperY2K on 2006-06-21
did you try it without the umask option?

---

### Post by mardok on 2006-06-21
[QUOTE=HyperY2K]did you try it without the umask option?[/QUOTE]

Thank you very much ! i didn't think this could be the reason :) but this was ! now ti works fine ! thanks !

---

### Post by HyperY2K on 2006-06-21
no problem, i've just look in the manual entry for pmount :wink: : 
```
FILES
       /etc/pmount.allow
              List  of  devices  (one  device per line) which are additionally
              permitted for pmounting.
```

---

### Post by Giga on 2006-06-25
i mount my other hds through right click, in " Computer" , then mount
pmount works because i added all my hds in /etc/pmount.allow

after that, i added the following lines to fstab:
/dev/sdb1       /media/sdb1     ntfs-fuse    auto,gid=1000,umask=0022    0    0
/dev/sda1       /media/sda1     ntfs-fuse    auto,gid=1000,umask=0022    0    0
/dev/sdb2       /media/sdb2     ntfs-fuse    auto,gid=1000,umask=0022    0    0
/dev/hdb1       /media/hdb1     ntfs-fuse    auto,gid=1000,umask=0022    0    0 


The ntf-use group is from the ntfs write support i got from:
[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=mount+hd](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=mount+hd)

Ok.. i reboot thinking my hds will be working with writing support, after all, they are listed in fstab.
After restart, they are not working.. and when i try to mount then through right click on " Computer"  i got the message:
mount: only root can mount /dev/sda1 on /media/sda1

What im doing wrong here?
Thx

---

### Post by gspotremover on 2006-06-25
This is related to the topic, but a splinter thread - as my problem is the same but has different requirements for a solution:

I am encountering the same issue with pmount when attempting to open an NTFS volume. 
But I am booting from a live cd as I am attempting data recovery on a h#rked winxp pro system, thus -- I cannot edit pmount.allow since it's on a cd.

Is there another way to access this windows volume without having to install ubuntu fully?




Thx for letting me break my ubuntu cherry in your forums. ;)

---

### Post by sonnywise on 2006-06-26
[QUOTE=gspotremover]This is related to the topic, but a splinter thread - as my problem is the same but has different requirements for a solution:

I am encountering the same issue with pmount when attempting to open an NTFS volume. 
But I am booting from a live cd as I am attempting data recovery on a h#rked winxp pro system, thus -- I cannot edit pmount.allow since it's on a cd.

Is there another way to access this windows volume without having to install ubuntu fully?




Thx for letting me break my ubuntu cherry in your forums. ;)[/QUOTE]


You can probably use: mount /dev/hdXY /mnt/ -t ntfs

specify the correct hard drive and partition changing hdXY with the correct one.

---

