---
title: "FSTAB, what am I doing wrong?"
date: 2009-05-27
forum: General Help
---

### Post by eriktheblu on 2009-05-27
I've done several searches, read a couple guides, and have had no success with automounting with FSTAB. I'm sure I just missed something small, but I'm a relatively new Ubuntu user so I'm not really sure where to start

So here's my situation:

I'm running 8.04 64 bit.
I have 2 internal hard drives (sda and sdb)
First internal (sda) has the system and /home. All that works fine.

The second (sdb) has 2 data partitions (one [sdb1] for video and music, one [sdb5] for World of Warcraft [I dual box]) There's also another swap partition, and a Windows partition that I'm not concerned about (I may be removing that later, but I'm not in any danger of running out of space).

I also have a Linkstation network attached storage that calls itself 'share'. The folder I use on it is also called 'share'. There are no usernames or passwords to access this server. When I access it through the Places menu, it displays as smb://share/share (it's set up as a Windows share).

What I would like to do:
I would like the video/music partition (sdb1) mounted on boot as /media/secondary, the WoW partition as ~/Games/WoWlite, and the Linkstation as /media/share.

What I've tried: Py-something that later calls itself 'Storage Device Manager'. This adds lines to my FSTAB that based on my reading seem appropriate.
```
/dev/sdb5 /home/eriktheblu/Games/WoWlite  ext2 defaults 0 0 
```
and
```
/dev/sdb1 /media/Secondary ext2 defaults 0 0
```

I've also tried to mirror the other lines of the FSTAB; it looked something like
```
#/dev/sdb5 
UUID=d7b0c30a-3832-46ff-92c6-316c16a9d312  /home/eriktheblu/Games/WoWlite  ext2 defaults 0 0  
```
I've done it with and without the #.

I derived the UUID with blkid (i.e. I didn't just make it up), it didn't help.

Neither of the partitions mount where I wanted them, but instead when they mount it is at /media/sdb1 and media/sdb5.

The server I have tried```
//share/share/                           /media/share  smb 0 0 
```and ```
//share/share/ /media/share smb guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0
```(no idea what this means, I copied it from somewhere)

I've also installed PyNeighborhood which only gives me a 'Failed to mount' error on clicking the shared folder.

I know these are only minor annoyances, But if nothing else this is an interesting exercise.

Thanks in advance for any help or direction.

---

### Post by madverb on 2009-05-27
It might be helpful if you read
```
man fstab
```
and also find out exactly what defaults do.

---

### Post by dmizer on 2009-05-27
Please post the output of the following commands:
```
sudo blkid
```
```
sudo fdisk -l
```
```
df -Th
```
```
cat /etc/fstab
```

---

### Post by eriktheblu on 2009-05-27
Reading the man.

sudo blkid:
```
/dev/sda5: TYPE="swap" UUID="7e0b37eb-9ede-431a-8793-38c01ab751fa" 
/dev/sdb5: UUID="d7b0c30a-3832-46ff-92c6-316c16a9d312" TYPE="ext2" 
/dev/sda6: TYPE="swap" UUID="fe516db7-8885-4fca-b05c-b2d60e564acf" 
/dev/sda7: UUID="909cea58-83e8-4516-852c-6c33e0d62c0b" TYPE="ext2" 
/dev/sda8: UUID="d066389f-675a-4053-9d62-94f36fa34409" TYPE="ext3" 
/dev/sda9: UUID="49fe69ce-d19d-435d-ac78-7f6d68901d9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="01e74c0c-892e-4751-8d4e-562a06924ccf" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="42874499-18a4-4fd5-99f4-a224477958dc" TYPE="ext2" 
/dev/sdb2: UUID="48E4FF24E4FF12C4" TYPE="ntfs" 
/dev/sdb4: TYPE="swap" UUID="fe03188b-606e-4c55-b168-8dde5d050c6a" 

```

sudo fdisk -l:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006c516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    5  Extended
/dev/sda5               1         127     1020064+  82  Linux swap / Solaris
/dev/sda6           38786       38913     1028128+  82  Linux swap / Solaris
/dev/sda7             128         158      248976   83  Linux
/dev/sda8             159        3805    29294496   83  Linux
/dev/sda9           26628       38785    97659103+  83  Linux
/dev/sda10           3806       16983   105852253+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75f3568e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23662   190064983+  83  Linux
/dev/sdb2   *       23663       26916    26137755    7  HPFS/NTFS
/dev/sdb3           26917       30146    25944975    5  Extended
/dev/sdb4           30147       30401     2048287+  82  Linux swap / Solaris
/dev/sdb5           26917       30146    25944943+  83  Linux

```

df -Th
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda8     ext3     28G  3.9G   23G  15% /
varrun       tmpfs    2.0G  312K  2.0G   1% /var/run
varlock      tmpfs    2.0G     0  2.0G   0% /var/lock
udev         tmpfs    2.0G   84K  2.0G   1% /dev
devshm       tmpfs    2.0G   12K  2.0G   1% /dev/shm
lrm          tmpfs    2.0G   45M  1.9G   3% /lib/modules/2.6.24-24-generic/volatile
/dev/sda7     ext2    228M   38M  179M  18% /boot
/dev/sda9     ext3     93G   20G   69G  22% /home
/dev/sdb5     ext2     25G   17G  7.3G  70% /media/sdb5
/dev/sdb1     ext2    180G   37G  135G  22% /media/sdb1
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     28G  3.9G   23G  15% /home/eriktheblu/.gvfs

```

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                           proc         defaults                    0  0  
# /dev/sda8
UUID=d066389f-675a-4053-9d62-94f36fa34409  /                               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda7
UUID=909cea58-83e8-4516-852c-6c33e0d62c0b  /boot                           ext2         relatime                    0  2  
# /dev/sda9
UUID=49fe69ce-d19d-435d-ac78-7f6d68901d9d  /home                           ext3         relatime                    0  2  
# /dev/sda5
UUID=365acf20-b403-4eaf-b944-7b79efc1369e  none                            swap         sw                          0  0  
# /dev/sda6
UUID=fe516db7-8885-4fca-b05c-b2d60e564acf  none                            swap         sw                          0  0  
# /dev/sdb4 
UUID=fe03188b-606e-4c55-b168-8dde5d050c6a  none                            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0                   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb5 
UUID=d7b0c30a-3832-46ff-92c6-316c16a9d312  /home/eriktheblu/Games/WoWlite  ext2         defaults                    0  0  


# //share/share/                           /media/share                    smb          guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  

/dev/sdb1                                  /media/Secondary                ext2         defaults                    0  0 
```

---

### Post by dmizer on 2009-05-27
Okay ... let's get your hdd partitions mounted. First of all, they're currently mounted in /media/sdb5 and /media/sdb1, so you'll have to unmount them:
```
sudo umount /media/sdb5
sudo umount /media/sdb1
```

Then, you'll need to make a couple of edits to your current /etc/fstab as follows
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                           proc         defaults                    0  0  
# /dev/sda8
UUID=d066389f-675a-4053-9d62-94f36fa34409  /                               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda7
UUID=909cea58-83e8-4516-852c-6c33e0d62c0b  /boot                           ext2         relatime                    0  2  
# /dev/sda9
UUID=49fe69ce-d19d-435d-ac78-7f6d68901d9d  /home                           ext3         relatime                    0  2  
# /dev/sda5
UUID=365acf20-b403-4eaf-b944-7b79efc1369e  none                            swap         sw                          0  0  
# /dev/sda6
UUID=fe516db7-8885-4fca-b05c-b2d60e564acf  none                            swap         sw                          0  0  
# /dev/sdb4 
UUID=fe03188b-606e-4c55-b168-8dde5d050c6a  none                            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0                   udf,iso9660  user,noauto,exec,utf8       0  0  
[s][COLOR="Red"]/dev/sdb5 [/s] !! remove this line !![/COLOR]
# /dev/sdb5
UUID=d7b0c30a-3832-46ff-92c6-316c16a9d312  /home/eriktheblu/Games/WoWlite  ext2         relatime,errors=remount-ro 0	1
# /dev/sdb1
UUID=42874499-18a4-4fd5-99f4-a224477958dc  /media/Secondary                ext2         relatime,errors=remount-ro 0	1


# //share/share/                           /media/share                    smb          guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0  

[COLOR="Red"][s]/dev/sdb1                                  /media/Secondary                ext2         defaults                    0  0[/s] !! remove this line !![/COLOR]
```
Then run this command:
```
sudo mount -a
```
If you get errors after that command, post them. If not, your partitions should be mounted. Once that's working correctly, then we'll get your NAS device mounted.

---

### Post by eriktheblu on 2009-05-27
As is typical of my luck, after posting all of this, the mounting of the internal drives suddenly decided to work this morning after a reboot.
(note to self: sudo mount -a before bothering the nice people of the Ubuntu forums)

After another reboot, /dev/sda and /dev/sdb decided to swap names (is this normal? This has happened a couple of times)

I think I have the internal drives working now, and they are both identified in FSTAB  by UUID.

Current FSTAB
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc                           proc         defaults                    0  0  
# /dev/sda8
UUID=d066389f-675a-4053-9d62-94f36fa34409  /                               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda7
UUID=909cea58-83e8-4516-852c-6c33e0d62c0b  /boot                           ext2         relatime                    0  2  
# /dev/sda9
UUID=49fe69ce-d19d-435d-ac78-7f6d68901d9d  /home                           ext3         relatime                    0  2  
# /dev/sda5
UUID=365acf20-b403-4eaf-b944-7b79efc1369e  none                            swap         sw                          0  0  
# /dev/sda6
UUID=fe516db7-8885-4fca-b05c-b2d60e564acf  none                            swap         sw                          0  0  
# /dev/sdb4 
UUID=fe03188b-606e-4c55-b168-8dde5d050c6a  none                            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0                   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb5 
UUID=d7b0c30a-3832-46ff-92c6-316c16a9d312  /home/eriktheblu/Games/WoWlite  ext2         defaults                    0  0  
# /dev/sdb1 
UUID=42874499-18a4-4fd5-99f4-a224477958dc  /media/Secondary                ext2         defaults                    0  0  
```

sudo mount -a correctly mounts the 2 drives, but still returns
```
mount: mount point  does not exist

```
I assume this is referring something else I hosed. (could be one of my swaps; system monitor shows me 1GB short)


A new development; after trying some guides and installing random packages, I can no longer even browse the server. I can still access files directly (e.g. a couple of audio files under Places>>Recent Documents). I can also access it by opening files in an application (e.g. Gimp). For some reason Nautilus tells me: 'Couldn't display "smb://share/share/". There is no application installed for this file type'.

smbfs package is installed.

I'm tempted to reinstall or upgrade the OS.

[OK, fixed this with a 'nautilus smb://share/share', but automounting still not working]

---

### Post by dmizer on 2009-05-27
You are getting this error:
```
mount: mount point  does not exist

```
Because you forgot to add the "#" in front of /dev/sdb5 (above your WoWlite drive)

> **eriktheblu said:**
> ```
[COLOR="Red"]**# **[/COLOR]/dev/sdb5
```

Unfortunately, it has become normal for drives to change device locations after booting. This is one reason why we use UUID instead now.

Please post the output of:
```
smbtree
```

---

### Post by eriktheblu on 2009-05-27
> **dmizer said:**
> 
Because you forgot to add the "#" in front of /dev/sdb5 

I see.....

The # is either conspicuously omitted or inconspicuously mentioned in the literature I've seen. I'm guessing this a sort of error suppression?

smbtree:
```
ETB
	\\SHARE          		Link Station

```

I just finished playing around with the server mount line and wound up with
```
//share/share                              /media/share			   cifs 		user=guest,password=			    0  0
```

This worked with the sudo mount -a.

When I had # at the beginning of the beginning of the line it failed to mount.

I genuinely appreciate all the help. Hopefully I'll be able to repeat these results in the future.

---

### Post by dmizer on 2009-05-27
> **eriktheblu said:**
> I see.....

The # is either conspicuously omitted or inconspicuously mentioned in the literature I've seen. I'm guessing this a sort of error suppression?
No, it's a cross platform standard for comments. Too well known to mention in any manuals. More information here: [http://en.wikipedia.org/wiki/Comment_(computer_programming)](http://en.wikipedia.org/wiki/Comment_(computer_programming))

> **eriktheblu said:**
> smbtree:
```
[CODE]//share/share                              /media/share			   cifs 		user=guest,password=			    0  0
```

This worked with the sudo mount -a.
If that works, stick with it! :)

---

