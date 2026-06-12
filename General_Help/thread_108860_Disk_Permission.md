---
title: "Disk Permission"
date: 2005-12-27
forum: General Help
---

### Post by Yuanlong on 2005-12-27
I've problem trying to get permission to write to partition on my hard drive.  The partition infomation from the property tab are

File Owner: root
File group: root

Owner: Read, Write, Execute
Group: Read, Execute
Others: Read, Execute

Text View: drwxr-xr-x
Number View: 755

*You are not the owner, so you can't change these permission

I'm not too good with command lines so I can't find a way to change the permission.  I've tried logging in as root but it tell me that there are no such user.

---

### Post by Koybe on 2005-12-27
Use this on a comand line, you'll be able to browse as an adminsitrator.
```
sudo nautilus
```

---

### Post by kosmic on 2005-12-27
and have a look at the man page of chmod 
 
in terminal : man chmod
and also man chown

---

### Post by Yuanlong on 2005-12-27
[QUOTE=Koybe]Use this on a comand line, you'll be able to browse as an adminsitrator.
```
sudo nautilus
```[/QUOTE]

I've used "sudo nautilus" to browse with adminsitrator permission but still I can't change the permission.  Whenever I checked the write option, it will be unchecked immediately.

[quote=kosmic]and have a look at the man page of chmod

in terminal : man chmod
and also man chown[/quote]

I've look through these 2 document, but I can't get an idea how the command should look like?  Can you give me an example?  Lets say if my drive is hda5, is this how I should type the command?
chmod -c a+w /media/hda5

Sorry for being such a noob :(

---

### Post by fordfan753 on 2005-12-27
Recursive permissions in Nautilus are broken, soon to be fixed though. :D

What partition do you want rw access to? Is it your root partition? (/) If it is, then it's a bad idea, if not, I'm sure you could use mount options to get access to it.

---

### Post by fordfan753 on 2005-12-27
Oh, and can I get a dump of your /etc/fstab file? Thanks

---

### Post by Yuanlong on 2005-12-27
[QUOTE=fordfan753]Recursive permissions in Nautilus are broken, soon to be fixed though. :D

What partition do you want rw access to? Is it your root partition? (/) If it is, then it's a bad idea, if not, I'm sure you could use mount options to get access to it.[/QUOTE]

No, I just want rw access to my hda5 partition.  Which is the largest partition on my hard drive for storing data.

Edit: Included /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by fordfan753 on 2005-12-27
What is the filesystem type on that partition?

---

### Post by fordfan753 on 2005-12-27
Change
```
/dev/hda5       /media/hda5     vfat    defaults        0       0
```
to
```
/dev/hda5       /media/hda5     vfat    rw,user,umask=000        0       0
```

Then:
```
sudo mount -a
```
or simply reboot

---

### Post by Yuanlong on 2005-12-27
That solve the problem.  Thanks a lot

---

### Post by fordfan753 on 2005-12-27
[QUOTE=Yuanlong]That solve the problem.  Thanks a lot[/QUOTE]

Cool! Glad to hear it :)

---

