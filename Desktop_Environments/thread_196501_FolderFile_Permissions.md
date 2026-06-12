---
title: "Folder/File Permissions"
date: 2006-06-14
forum: Desktop Environments
---

### Post by GmAz on 2006-06-14
Ok.  I copied a folder with many files and subfolders onto my computer under the root account.  It was a weird hard drive mounting issue.  Anywho, I copied them to my own account's desktop, not root's desktop.  Now, everything is locked because I did this under root.  Thinking like in windows when you give permissions, I set the owner and group to my account thinking it will apply to all subdirectories as well.  Well, it doesn't.  Is there a way to do this.  If not, I will have to change the permissions for every freaking file and folder.  Thats a lot of work.  Any help would be great.  Thanks.

---

### Post by ayoli on 2006-06-14
in a terminal type:
sudo chown -R your_username.your_groupname /path/you/want

that's change recursively owner and group for all folder/files in /path/you/want

then 
sudo chmod -R u+rwx /path/you/want

will make all that files folders readable/writeable/executable by you, but you may not want to have same perm for all files on your desktop.

cheers

---

### Post by GmAz on 2006-06-14
Perfect, that helped tons.  Now the second part.  I have three hard drives in my system.  One that Ubuntu is on, another one that used to part of my Raid0 array that no longer exists and a third that is just used for backup storage.  I can see the one I used for backup storage (200GB), but I can't open it or do anything with it.  Says I don't have permission.  I can't open it in root either.  The Owner and Group on it are 'unknown'.  If worse comes to worse, I can format it, but how do i do that?  Also, the other hard drive that was part of the raid array I want to use also, but I can't even see that one.  on System > Administration > Disks it recognizes as /dev/sdc but I can't access it anywhere.  Any help would be great.  Thanks.

---

### Post by Ramses de Norre on 2006-06-14
Could you post the output of ```
sudo fdisk -l && cat /etc/fstab
```

---

### Post by GmAz on 2006-06-14
Here are the results:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30024   241167748+  83  Linux
/dev/sdb2           30025       30401     3028252+   5  Extended
/dev/sdb5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

[[Side note]]

I have two DVD burners in my comptuer but only one shows up in my Places > Computer window.  Is this correct?  It may be minor, but I went full on Linux and got rid of WinXP so I would like get it working and know how to do it too.  Being a computer tech and not knowing how to do my own 'fix-its' is frustrating  =).

---

### Post by dykesy61 on 2006-06-15
I am still having problems working out how this all works, being a newbie!
I have 2 hard drives, and can save stuff to my profile directory.
but I cannot to the other drive - ROOT is the owner, and I can't change that no matter what I try!
help please - what do I need to do?

and.
as I am the only user on this system, is there a way I can change my own users permissions to be the same as ROOTs?

any help gladly accepted - thanks!

---

### Post by GmAz on 2006-06-15
Ok, if you can actually see your second hard drive having the permissions of root, then you can log into the root account and change those.  I however see unknown for the permissions on one hard drive and can't even see the other hard drive.  To log into root, you need to go to:
System > Administration > Login Window click on the Security and check box the Allow local system administrator login.  Then you can login as root from the login screen.  Make sure you do:
sudo passwd root
in the terminal and change the root password to whatever you want.  Now you can login as root and change the permissions.  If that doesnt work for you, then you are in the same boat as I am.

On the second part, you really don't want the same permissions as root because if you get a virus or a hacker tries to have some fun, then he has full permission.  That is why you are always asked for a password and have to use the *sudo* command in the terminal and enter your password.

---

