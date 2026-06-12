---
title: "Changing permissions"
date: 2005-12-05
forum: Desktop Environments
---

### Post by ashrack on 2005-12-05
1.How to change READ/WRITE permission also on the subfolders/files
I already replaced ownership with this command which also included all the subfolders and files:
```
sudo chown -L -R tom ./Mozilla
```

2.I can only access NTFS partition if am root. And if I use "chown" it says the partition is read only and thus it cannot change the ownership.
NFTS partition is mounted at /media/hda1
```
sudo chown -L -R tom /media/hda1
```

---

### Post by kosmic on 2005-12-05
[quote=ashrack]1.How to change READ/WRITE permission also on the subfolders/files
I already replaced ownership with this command which also included all the subfolders and files:
```
sudo chown -L -R tom ./Mozilla
```
 
2.I can only access NTFS partition if am root. And if I use "chown" it says the partition is read only and thus it cannot change the ownership.
NFTS partition is mounted at /media/hda1
```
sudo chown -L -R tom /media/hda1
```[/quote]
 
 
To change READ/Write permissions in subfolders and/or files do :
 
sudo chmod 666 -R /foldername
 
If you want READ/WRITE/EXECUTE for USER - GROUP - OTHERS do
 
sudo chmod 777 -R /foldername
 
TO acess NTFS partitions as a user edit the file /etc/fstab as root and add the option 'users' and 'umask=000' to the partition you want user can acess

---

### Post by ashrack on 2005-12-05
Any chance I could set CHMOD permissions using GUI

---

### Post by Niall Flinn on 2005-12-05
Hi, I'm new here too, but AFAIK, you can chmod via the nautilus file browser - just right-click on the file(s) you want to chmod and go to the permission tab, then click on the check boxes to set permissions. 

It's a bit awkward though, because you'll need to start nautilus from a shell as superuser:

**sudo nautilus**

And then you don't seem to have the option to recursively set permissions via the GUI...  so you're probably better off getting used to using the command line version, which is faster and more powerful anyway...

HTH,

Niall

---

### Post by ekarni on 2005-12-05
You can also use the following with chmod at the command line to make it a little easier:

chmod WHO +/- WHAT target

where WHO is _U_ser, _G_roup, _A_ll and WHAT is _R_ead, _W_rite, e_X_ecute.  So for example:

chmod a+rx foo.pl 

gives everyone read and execute permissions on foo.pl

---

### Post by ashrack on 2005-12-06
[QUOTE=Niall Flinn]Hi, I'm new here too, but AFAIK, you can chmod via the nautilus file browser - just right-click on the file(s) you want to chmod and go to the permission tab, then click on the check boxes to set permissions. 
[/QUOTE]
U can't. Because it wont go into subfolders. It will only CHMOD permisions on files and folders that are selected but not within those folders.
Any way to add it? So on the Nautilus GUI U would have the option to change permission on all folders and subfolders?

---

### Post by donvella on 2005-12-06
[QUOTE=kosmic]To change READ/Write permissions in subfolders and/or files do :
 
sudo chmod 666 -R /foldername
 
If you want READ/WRITE/EXECUTE for USER - GROUP - OTHERS do
 
sudo chmod 777 -R /foldername
 
TO acess NTFS partitions as a user edit the file /etc/fstab as root and add the option 'users' and 'umask=000' to the partition you want user can acess[/QUOTE]

Please elaborate, I added users, umask=000 to "Options" in fstab and it still didnt alow me access to NTFS partition.

---

### Post by kosmic on 2005-12-06
ok
> 
A typical fstab looks something like the following: 
 
## /etc/fstab## 
<device> <mountpoint> <filesystemtype><options> <dump> <fsckorder>
 
/dev/hdb5 / ext2 defaults 1 1
 
/dev/hdb2 /home ext2 defaults 1 2
 
/dev/hdc /mnt/cdrom iso9660 noauto,ro,user 0 0
 
/dev/hda1 /media/dos_c msdos **users**,defaults **umask=000** 0 0
 
/dev/hdb1 /media/dos_d msdos **users**,defaults **umask=000** 0 0
 
none /proc proc defaults

 
It should look something like this :)

---

### Post by penguinman007 on 2005-12-06
[QUOTE=ashrack]Any chance I could set CHMOD permissions using GUI[/QUOTE]


That would be great.

I want root access to files and folders and I want to be able to open them and change them from a gui.

Is there a windows file explorer for linux ?

---

### Post by hollowhead on 2005-12-06
Cheers thats dead useful on the folder permissions.  Its not the type of thing that they put in linux books.

---

### Post by Slartibartfast on 2005-12-06
Hello!

I'm having some trouble getting the permissions right. I can't access my mounted NTFS hd's. My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults 0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults 0       0
/dev/sda2       /media/sda2     ntfs    users,defaults umask=000 0 0
/dev/sda4       /media/sda4     vfat    defaults 0       0
/dev/sda5       /media/sda5     ntfs    users,defaults umask=000 0 0
/dev/hdb1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Please, could someone tell me what I'm doing wrong!?!? :confused: 

//Slartibartfast

---

### Post by lcg on 2005-12-06
[QUOTE=Slartibartfast]
I'm having some trouble getting the permissions right. I can't access my mounted NTFS hd's. My fstab looks like this:
```

/dev/sda2       /media/sda2     ntfs    users,defaults umask=000 0 0
/dev/sda5       /media/sda5     ntfs    users,defaults umask=000 0 0

```
[/QUOTE]
Notice the space before umask: umask belongs to options and is separated from other options with a comma. Try something like this:
```
/dev/sda2       /media/sda2     ntfs    users,defaults,umask=000 0 0

```
However, this gives you 777 permissions on both files and directories, even though NTFS is read only and I usually don't have any useful executables on NTFS partitions (at least not useful for Linux). So I prefer this way:
```
/dev/sda2       /media/sda2     ntfs    users,defaults,dmask=222,fmask=333 0 0

```
And if you're using somthing other than plain ASCII on your NTFS partition, you should also add an option to tell your kernel what charset to use (UTF-8 ):
```
/dev/sda2       /media/sda2     ntfs    users,defaults,dmask=222,fmask=333,nls=utf8 0 0

```
Try this one. ;)

HTH,
Lars

---

### Post by towsonu2003 on 2005-12-06
edit - sorry (bad reading on my part)

---

### Post by ashrack on 2005-12-06
Remember in my previous linux distro MAndrake I could set all of those permision that I had to manually input into FSTAB with a GUI utility. 
Is there one here?
btw. I've forgoten how do I restart "/etc/fstab" 
I know there is way without having to: init 1 and then init 5 to get back to GUI

OFFTOPIC
And now off to changing the kernel

---

### Post by ashrack on 2005-12-06
How to remount /etc/fstab without rebooting?

sudo umount -a    (2 unmount all that is in /etc/fstab)
sudo mount -a      (2 mount all that is in /etc/fstab)


OFFTOPIC:
Still havent replace the kernel, since I was looking for the above sollution :p 
And now hopefully I will manage

---

### Post by bunty on 2005-12-06
[QUOTE=ashrack]1.How to change READ/WRITE permission also on the subfolders/files
I already replaced ownership with this command which also included all the subfolders and files:
```
sudo chown -L -R tom ./Mozilla
```

2.I can only access NTFS partition if am root. And if I use "chown" it says the partition is read only and thus it cannot change the ownership.
NFTS partition is mounted at /media/hda1
```
sudo chown -L -R tom /media/hda1
```[/QUOTE]

As Icq pointed out ntfs kernel driver is write only so you can neither change  perms.

I guess what you are trying to do is use the same installation of mozilla from both OS. This was done sucessfully by  a freind of mine but I'm pretty sure it was on vfat .

To cut all the details I think the best way forward would be to install a new copy of moz on a vfat partition under win and then try to import your email etc to the new one . 

From there you should be able to install linux mozilla and tell it to use the same directories for email etc. from the vfat by editing prefs.js on linux.

HTH

---

### Post by mcmunt on 2005-12-06
[QUOTE=bunty]As Icq pointed out ntfs kernel driver is write only so you can neither change  perms.[/QUOTE]

I'm pretty sure that should be **read only**. ;)

---

### Post by Sokraates on 2005-12-07
Maybe this is a little off-topic, but is there a way to have permissions automatically changed, once a file is put into a certain folder?

My wife and me use a shared folder for photos and other files we both use. The only problem is, that we have to change a file's group manually before moving it to this folder, otherwise the file can not be modified my the other. BTW: Im talking about a solution without NFS or samba.

---

### Post by aysiu on 2005-12-07
Can't you both be in the same group?

---

### Post by Sokraates on 2005-12-07
[QUOTE=aysiu]Can't you both be in the same group?[/QUOTE]

For security reasons I'd rather not automatically have all users belong to the same group (correct me if I'm writing rubbish; I'm still a linux-newbie). 

There is a special group for the shared folder, but I have te chgrp every file manually, when moving it to the shared folder (okay, there's "chgrp -R specialgroup /sharedfolder", still it has to be done manually).

---

### Post by ashrack on 2005-12-07
[I][COLOR="Red"]
1. In "nautilus" U can change permission and read/write/execute option thru GUI, but if U want it done recursive so all the subfolders will be changed also, U're best bet is using the following "chmod -R 777 /name_of_program/" 
Could this also be done thru GUI, like an option in NAUTILUS PERMISSION TAB to change all of them recursively so also the sub folders would be affected and not only what is selected?

2.In Mandriva there was a GUI program for mounting drives, changing them premissions, anything U need for changing "/etc/fstab" Is there one here?







[/COLOR][/I]

---

