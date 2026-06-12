---
title: "Storage Device Manager"
date: 2011-10-01
forum: Desktop Environments
---

### Post by Aleksiy on 2011-10-01
After installed Storage Device Manager can not remove "mount file system in read-only mode" option.

---

### Post by Rubi1200 on 2011-10-02
Hi and welcome to the forums :-)

I haven't used this tool but are there options for editing preferences?

Please also provide us with more information such as error messages etc. that would help us.

Thanks.

---

### Post by Copper Bezel on 2011-10-02
Storage Device Manager, as in pysdm, the GUI fstab editor?

---

### Post by Aleksiy on 2011-10-02
There is no options for editing preferences

---

### Post by Aleksiy on 2011-10-02
There is no options for editing preferences

"Storage Device Manager, as in pysdm, the GUI fstab editor?"  - Yes

---

### Post by Copper Bezel on 2011-10-02
So, when you have that partition selected, is the "Assistant" button just grayed out? Can you edit the text in the field?

---

### Post by Aleksiy on 2011-10-02
Yes I can edit the text in the field, but it does not help. May e I do something wrong, but read-only always stay marked

---

### Post by Copper Bezel on 2011-10-02
Weird. I assumed that PySDM only read from fstab, so it shouldn't know anything you don't. = ) 

Is it one specific partition that it won't let you edit permissions on, or does it apply to all of them? If it's specific, what kind of drive or partition is it?

If you do make changes in the text field, do they stick? Remember that the text string is the important part (where the settings are actually being changed to write to fstab) and that the difference will only be visible after a reboot.

---

### Post by Aleksiy on 2011-10-02
It is  applied to all of them.
If I do make changes in the text field, they are stick. I just Linux user and not familiar with it, so I changed ro to rw , added user - did not help.

---

### Post by Copper Bezel on 2011-10-02
What partitions are you trying to add read-write access to? Are they partitions on the internal hard drive, or a secondary or external drive you've added?

---

### Post by Morbius1 on 2011-10-02
Why not post the output of the following commands so we all know what you are talking about and so that we can help you fix it:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```
```
mount
```

---

### Post by Aleksiy on 2011-10-02
I just want to restore my system, which was worked fine till I try Storage Device Manager.
I have Windows and Ubuntu on my PC. So no Ubuntu volumes I can not control now.

---

### Post by Copper Bezel on 2011-10-02
Yeah, in that case, seriously, just post the contents of /etc/fstab and let one of us fix it for you. It'll be a lot easier than diagnosing the problem with Storage Device Manager.

---

### Post by Aleksiy on 2011-10-02
[COLOR=Purple]sudo blkid -c /dev/null[/COLOR][COLOR=Purple]

/dev/sda1: LABEL="System Reserved" UUID="F0206D20206CEF52" TYPE="ntfs" 
/dev/sda2: UUID="C2EA71C3EA71B46F" TYPE="ntfs" 
/dev/sdb1: UUID="a2e03138-663e-4e80-b401-6dce42182eb4" TYPE="ext4" 
/dev/sdb2: UUID="a72c9110-41bd-41da-beba-e661b05d89b0" TYPE="swap" 
/dev/sdb3: LABEL="Storage" UUID="84F6A62DF6A62002" TYPE="ntfs" 
/dev/sdc1: LABEL="Marvin" UUID="147AE1DF7AE1BE1C" TYPE="ntfs" 
/dev/sdd1: LABEL="Video" UUID="605C-C462" TYPE="vfat" [/COLOR]

[COLOR=Sienna]aleksiy@Ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid         0  0  
/dev/sdb1                                  /            ext4  defaults                    0  1  
# swap was on /dev/sdb2 during installation
UUID=a72c9110-41bd-41da-beba-e661b05d89b0  none         swap  sw                          0  0  
/dev/sdb3                                  /media/sdb3  ntfs  nls=iso8859-1,rw,umask=000  0  0  
/dev/sdc1                                  /media/sdc1  ntfs  nls=iso8859-1,rw,umask=000  0  0 
[/COLOR]
[COLOR=Green]
aleksiy@Ubuntu:~$ mount
/dev/sdb1 on / type ext4 (rw,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb3 on /media/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aleksiy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aleksiy)
/dev/sdd1 on /media/Video type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
[/COLOR]
I removed line for /dev/sdd1in etc/fstab and now usb card memory looks like restore to normal.
But sdb3 and sdc1 I  (Windows storage HDD and Raid0 )can not unmount and remount ( and I have a writing privileges now)

---

### Post by Morbius1 on 2011-10-02
> But sdb3 and sdc1 I  (Windows storage HDD and Raid0 )can not unmount and remount ( and I have a writing privileges now) 	
> [COLOR=Sienna]/dev/sdb3                                  /media/sdb3  ntfs  nls=iso8859-1,rw,umask=000  0  0  
/dev/sdc1                                  /media/sdc1  ntfs  nls=iso8859-1,rw,umask=000  0  0 [/COLOR]

Those 2 lines will mount automatically at boot those 2 ntfs partitions with r/w/x access to everyone. You have no need to unmount them. That's why you put them in fstab.

I don't understand the nature of the problem.

---

### Post by Aleksiy on 2011-10-02
The problem is in Storage Device Manager bugs. It screwed up my system. I corrected fstab manually - thanks all of you, who help me ):P. But I spent two days for it. And still not understand why I can not manually unmount and remount them now. And I am going to remove Storage Device Manager from my system, but afraid it will changed something again if I will do it. Because Storage Device Manager still have read-only option marked on my volumes - I can not unmarked it. I do not know , how it is working.

---

