---
title: "Not sufficient user privileges to Read/write to NTFS drives"
date: 2006-08-06
forum: Desktop Environments
---

### Post by vinitlee on 2006-08-06
I have a collection of NTFS partitions alongside my ext3 system partition for Ubuntu. I added these NTFS-populated drives after installation, so they were not accounted for within the Ubuntu install.

Currently, I am trying to access these partitions, for the system sees them, but I do not have sufficient privileges to access them in any way unless I am root.

I would like a way to at least read these drives from any user.

Has anyone run into a similar problem and/or have a solution for it?

Any help appreciated.

---

### Post by dennisharrison on 2006-08-06
chmod 777 */ntfs drive* 
chgrp *yourusergroup* */ntfs drive*

does that do anything?

do an ls -l on the directory to see what the output is

---

### Post by vinitlee on 2006-08-06
chmod: changing permissions of `/tmp/disks-conf-hda1/': Read-only file system

That comes up when I try chmod-ing

---

### Post by mssever on 2006-08-06
Chmoding the files won't work because the NTFS filesystem doesn't support the Linux permission model. You have to edit your /etc/fstab and find the line that refers to your NTFS partition. If you only need to access the files using a single user, change the column defaults to defaults,uid=1000 (assuming that you're using the account created when you installed Ubuntu). You might also want to add the ro option to mount the partition as read-only, since writing to NTFS partitions is not yet considered safe.

If you need a more advanced setup, you can set a umask at the same place. Here's a line from my fstab:
```
/dev/hda1  /media/hda1  ntfs   defaults,nls=utf8,umask=007,gid=46,ro  0  1

```

EDIT: I forgot to mention that you need to remount the partition (or reboot) for the changes to take effect.

EDIT 2: If it is feasible, you might want to consider reformatting the NTFS partitions to use FAT32 (Linux: vfat). This way, you can safely read and write in Linux and Windows.

---

### Post by 3rdalbum on 2006-08-06
You don't change the permissions of the file system itself... you change the permissions that Linux assigns to the partition.

Open up /etc/fstab (sudo nano /etc/fstab). For each NTFS partition, under the <Options> column, you must put:

```
nls=utf8,umask=0222
```

That will allow your normal user to read the partition.

---

### Post by vinitlee on 2006-08-07
Thank you mssever and 3rdalbum for those tips, I've edited the fstab and they're mounting fine now.:D

---

### Post by n00buntu on 2006-08-07
Hello,
   I have the same problem with mounting my partition.  My fstab looks like this:

/dev/hda1    /media/hda1    ntfs    defaults,nls=utf8,umask=007,gid=1001   0    0

Am I missing something?  Thank you for any advice you can give me.

---

### Post by mssever on 2006-08-07
> **n00buntu said:**
> Hello,
   I have the same problem with mounting my partition.  My fstab looks like this:

/dev/hda1    /media/hda1    ntfs    defaults,nls=utf8,umask=007,gid=1001   0    0

Am I missing something?  Thank you for any advice you can give me.

Do you have a group with gid 1001 on your system? If so, it should work. Everything looks OK. Try remounting with [FONT="Courier New"][COLOR="SeaGreen"]mount -o remount /media/hda1[/COLOR][/FONT]. If that doesn't work, try rebooting (technically you don't have to reboot, but sometimes it's easier).

---

### Post by vinitlee on 2006-08-07
Personally, I used "user" isntead of a gid, making it accessable to everyone.

---

### Post by n00buntu on 2006-08-08
I tried "user" and I tried "uid=1000" but it doesn't seem to work.  Sometimes I get a message that says "mount point /media/hda1 does not exist."  My fstab now says:

/dev/hda1    /media/hda1    ntfs    defaults,nls=utf8,umask=007,uid=1000   0    0

By the way, I don't get the message about only root can mount, so I think one problem seems solved.  Thank you to everyone for their help so far.

---

### Post by mssever on 2006-08-08
> **n00buntu said:**
> Sometimes I get a message that says "mount point /media/hda1 does not exist."

Browse to /media/hda1 and make sure that it does, in fact, exist. Also make sure that it's empty (when hda1 isn't mounted).

---

### Post by n00buntu on 2006-08-09
It does not exist.  I cannot seem to mount the drive.

---

### Post by mssever on 2006-08-10
> **n00buntu said:**
> It does not exist.  I cannot seem to mount the drive.

The reason that you can't mount the partition is because the mount point doesn't exist (like the error message says; see my previous post). Create the mount point and it sould work.```
sudo mkdir -p /media/hda1
```

---

### Post by n00buntu on 2006-08-14
That was the problem.  I followed your instruction to mkdir, and now it mounts correctly!  It took me weeks to figure this out, and your solution was so easy!  Thank you again to everyone for their help!

---

