---
title: "how can I see all mounted partitions on Gnome Deskop ?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by choub08 on 2006-05-08
Hi,
Only my mounted NTFS partitions are visible on Gnome desktop or Nautilus. 
I would like to see also ext3 one  (like /home). I have tried to update my /etc/fstab file to add an umask as other partition but without strong sucess to be honest.

If one of you could give me some tips or best a solution. It would help me a lot. Please find hereinafter a copy of my fstab file...
Thanks in advance for your help 
F.

--
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       		<dump>  <pass>
proc            /proc           proc    defaults       			 0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 	 0       1
/dev/hda6       /home           ext3    defaults		       	 0       2
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222    		 0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222    		 0       0
#/dev/sda1       /media/sda1     ntfs    defaults        		 0       0
/dev/sdb5       /media/sdb5     ntfs   nls=utf8,umask=0222    		 0       0
/dev/hda7       /sharewin       vfat    iocharset=utf8,umask=0222  	 0       0
/dev/sdb6       none            swap    sw              		 0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     		0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  		0       0

---

### Post by ubuntu_demon on 2006-05-08
this is not a howto that's why I changed the title to a question.

---

### Post by Ramses de Norre on 2006-05-08
You wont achieve that in fstab, you shouldn't use a umask on your home folder.
The best way to do this are symlinks like this for home:```
ln -s ~ ~/Desktop/home
```

But for some folders you can turn them on in gconf: ```
gconf-editor /apps/nautilus/desktop
```
Turn on and name trash, home and documents to your likings. For other folders make a symlink. (man ln will show more info)

---

### Post by Omnios on 2006-05-08
K in menus go / Applications / System tools / Configuration Editor /
 In the editor go / " / " / Apps /  nautilus / desktop. 
 Now you can check mark Volumes visable which will now show your mounts there is also a checkmark for home folder and trash.

 Oopsies beet me to it.

---

### Post by matthewstory on 2006-05-08
read the mtab file

sudo nano /etc/mtab

---

