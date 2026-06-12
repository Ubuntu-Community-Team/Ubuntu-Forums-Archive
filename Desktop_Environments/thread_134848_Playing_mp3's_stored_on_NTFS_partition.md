---
title: "Playing mp3's stored on NTFS partition"
date: 2006-02-22
forum: Desktop Environments
---

### Post by gsplsngr on 2006-02-22
I can play mp3 that are loaded on ipod shuffle but can't play them from my NTFS partition...Tried to copy mp3 over to linux partition, but could not view it from my login

---

### Post by cskeide on 2006-02-22
sounds like a problem with user permissions for your ntfs partition.

edit /etc/fstab and add umask=0222 to the partition options.

Mine looks like this:

/dev/hda1       /media/WinXP    ntfs    ro,nls=utf8,umask=0222        0       0

---

### Post by byen on 2006-02-22
Yep..all you have to do is show your linux system where to find your ntfs partition. To make this happen everytime you bootup all you have to do is:
Open Terminal>
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
```

and then add the following at the end of the page:
```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```
where hda1 would be the partition where you have NTFS..now this may vary on your system so please check before adding it.
Hope that helps. Goodluck!

EDIT: just realised cskeide beat me to it :-)

---

### Post by gsplsngr on 2006-02-22
I am such the newbie....after I type in sudo gedit /etc/fstab and press enter it takes me to etc/fstab: static file systme information and does not allow me to enter anything. Am I at the write screen?

---

### Post by kaamos on 2006-02-22
Are you shure you had sudo in front of the command? Does the text editor title bar say "Read only" or not ?

---

### Post by gsplsngr on 2006-02-22
it says read only

---

### Post by kaamos on 2006-02-22
And you had sudo? Try this:
```
sudo su
```
What is normally a "$" should now be a "#" (if not, trouble). Then type
```
gedit /etc/fstab
```
And hope the readonly is gone.

---

### Post by gsplsngr on 2006-02-22
I tried it again an now it does not say read only

---

### Post by ronmarley1 on 2006-02-22
Great!  Now change the line to read (mine looks like this):
/dev/hda1       /media/hda1     ntfs    umask=0222        0       0
and then save the changes.  You may need to reboot, but I can't remember for sure.
That will allow you read access to ntfs partitions.  If you want to write to the Windows side, create a fat32 partition and mount that to write to it.  Although you can, you really don't want to give the Linux side write rights to the ntfs partition.  That can lead to disasterous results.

---

### Post by gsplsngr on 2006-02-23
Where do I put the code. /dev/hda1 /media/hda1 ntfs umask=0222 0 0 ? Here is the what information I am getting.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda6       /osshare        vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ronmarley1 on 2006-02-23
[QUOTE=gsplsngr]Where do I put the code. /dev/hda1 /media/hda1 ntfs umask=0222 0 0 ? Here is the what information I am getting.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda6       /osshare        vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0[/QUOTE]

The code I posted is for MY machine (I just included it as an example).  Your ntfs partition is mounted at:
/dev/hda2       /media/hda2     ntfs    defaults        0       0
In this line, change the word "defaults" to "umask=0222"
WITHOUT the quotes.  Then see my previous posting on what to do next.

---

