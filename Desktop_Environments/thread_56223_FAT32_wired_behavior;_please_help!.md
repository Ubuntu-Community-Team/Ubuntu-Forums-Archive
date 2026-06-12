---
title: "FAT32 wired behavior; please help!"
date: 2005-08-11
forum: Desktop Environments
---

### Post by alquimista on 2005-08-11
Hi,
I have my FAT32 partition to share files with WinXP; using Konkeror to navigate in it, I found the following problems:
1- I can move, rename,  copy all files there  but not delete them; the context menu in Konqueror is disabled for deletions. But its funny when in terminal, my normal user (not root) can delete files there.

2- Another wired thing I noticed, is that my user (gnajar) creates a file in the FAT32 partition, and in the file info it tells me that the  owner is "root"; wasn't it supposed to be gnajar?

3- I created a new folder; then when I refreshed the file tree in Konkeror, the folder was not there; what I found was a  text file that seems to contain folder metadata, and not the folder itself, After I tryed a 2nd time, it worked fine  :???: 

I have tryed several fstab lines as suggested in other NewsGroups, yet no one works so far. My last one is:

/dev/hda5       /media/datos    vfat    auto,umask=0,user,codepage=850,rw,exec  0       0

I have tryed before with:
/dev/hda5       /media/datos    vfat    auto,umask=0000,user,rw,exec  0       0
/dev/hda5       /media/datos    vfat    auto,umask=0000,quiet,uid=1000,rw,exec  0       0  (my user is 1000)

I have Kubuntu on a Toshiba Satellite A60. The full fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 unhide,ro,user,noauto  0       0
/dev/hda5       /media/datos    vfat    auto,umask=0,user,codepage=850,rw,exec  0       0


Any help will be appreciated, since this problem is bugging me since I installed Kubuntu, and I wanat ot have it as my main OS, releasing myself from WinXP.

Thanx,
Guillermo

---

### Post by alquimista on 2005-08-11
I discovered that what I though to be a FAT32 partition problem, was a Konqueror wired behavior: having the "detailed list" view of files, the delete option of the context menu is disabled. Having the normal view of files as incons, the option is there.
I have the spanish version; is it a bug?? if so.. where can I report it??? 


Guillermo

---

