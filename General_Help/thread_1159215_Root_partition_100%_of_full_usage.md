---
title: "Root partition 100% of full usage"
date: 2009-05-14
forum: General Help
---

### Post by luisjeronimo on 2009-05-14
hi, I have a problem with my root partition which gives me 100% of full usage can it be corrected?

I recently grow it up to 8GB, and I thought it was enough... What am I doing wrong? Please help..

---

### Post by sjuranic on 2009-05-14
Well, I'm taking a total guess as to what your fstab looks like (a copy would help to provide a clearer answer).

I find that /boot tends to grow a little out of control after a couple of kernel upgrades.  So the first thing I would do is to remove all of the images that I'm not using anymore (don't forget to remove them from the GRUB list as well).

Also, make sure you aren't hanging on to a bunch of old temporary files in /tmp (again, depending on what your fstab looks like)

That's really all the more specific my advice can be at this point.  Essentially your problem is you've got too much stuff in your root partition and you need to go in and remove some files.

---

### Post by luisjeronimo on 2009-05-14
here it's my fstab:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>			 <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=c1c58d9d-f317-4707-a4c7-5906eb1ef832 /               ext4    relatime,errors=remount-ro 0       1
# /home on /dev/sda5
UUID=f4af2fa6-6bd8-499e-9c93-41e59b7a69fa /home		ext4	nodev,nosuid,relatime 	0    2
# /media/WindowsXP on /dev/sda3
UUID=92E8D989E8D96BCB			/media/WindowsXP	ntfs-3g	auto		 0 0
#was on /dev/sda6 during installation
UUID=44771295-18ed-4ef5-ac48-e8f68fc40404 none            swap    sw              0       0

and my mtab:

/dev/sda7 / ext4 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-12-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda5 /home ext4 rw,nosuid,nodev,relatime 0 0
/dev/sda3 /media/WindowsXP fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/luis/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=luis 0 0

and even my fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bf73bf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14373       19457    40845262+   5  Extended
/dev/sda2               1        3352    26924908+  83  Linux
/dev/sda3   *        3353       14372    88518150    7  HPFS/NTFS
/dev/sda5           14373       18196    30716248+  83  Linux
/dev/sda6           19254       19457     1638598+  82  Linux swap / Solaris
/dev/sda7           18197       19253     8490321   83  Linux

---

### Post by drs305 on 2009-05-14
I recently wrote a guide on finding lost disk space. There is now a thread and a wiki, with links below. Most commonly, an ubuntu partition gets filled with either unemptied trash or a back up that was incorrectly written to the system partition instead of another drive.

Wiki Guide:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Trash:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by luisjeronimo on 2009-05-14
I do have tried it all, but it stills not working.. Give more hints please

---

### Post by whoop on 2009-05-14
```

baobab

```
Might tell you what is taking up all the space.

---

### Post by drs305 on 2009-05-14
> **luisjeronimo said:**
> I do have tried it all, but it stills not working.. Give more hints please

OK, run these commands so we can get a look at your disk:
```

df -Th | grep -v "fs" | sort 
sudo du -h --max-depth=1 / | sort

```

8GB should be enough space if you are using it only for the system. If you have lots of data stored in your /home folder you may simply not have enough space.

And for clarification, there is a system partition (all your system files) and a /root folder within the system partition, so don't confuse the two. I am assuming you don't have a separate /root partition.

Added: This is the original source of the wiki entry. At the bottom is a "5 Minute Guide" which condenses all the commands to run to try to troubleshoot disk space problems.

[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by luisjeronimo on 2009-05-14
for the first command the result:

```
/dev/sda3  fuseblk     85G   32G   53G  38% /media/WindowsXP
/dev/sda5     ext4     29G  7,0G   21G  26% /home
/dev/sda7     ext4    8,0G  8,0G     0 100% /
```

and for the second:

```
0	/proc
0	/sys
131M	/lib
14M	/boot
16K	/lost+found
16M	/etc
192M	/opt
2,7G	/usr
287M	/var
36G	/media
36M	/root
3,9M	/dev
4,0K	/mnt
4,0K	/selinux
4,0K	/srv
46G	/
48K	/tmp
6,5M	/bin
6,8G	/home
8,2M	/sbin
```

and I did a screenshot from baobab and it's anexed

---

### Post by drs305 on 2009-05-14
One of the suggestions I make in the wiki entry is to unmount non-system partitions before running most of the commands. The reason is that other partitions mounted in /media will show up and make it hard to find which *system* partitions are really full. One of the reasons is that you could have a backup file 'hidden' on /media, but it could be hidden because you have another partition mounted in the same place. You won't be able to 'see' it until you unmount the other partition.

In your case, you have some other partitions mounted on /media, which is why you can see 36G in /media even though you have an 8GB system partition (according to your first post).

Have you looked for undeleted trash?  See if you have files in these locations. If you do, use SHIFT-DEL to remove them - otherwise they will stay where they are.

```

gksu nautilus /root/.local/share/Trash/files
nautilus $HOME/.local/share/Trash/files

```

---

### Post by luisjeronimo on 2009-05-14
OK, so I get it... I did a backup with sbackup and it created a folder with the same name of my Backup partition.. 


Thank you everyone for your effort, I did resolve my problem

---

### Post by drs305 on 2009-05-14
> **luisjeronimo said:**
> OK, so I get it... I did a backup with sbackup and it created a folder with the same name of my Backup partition.. 


That is a very common problem - you aren't the first one to have this happen. Glad you were able to figure it out.

---

### Post by luisjeronimo on 2009-05-14
I added to sbackup config to not backup if the partition isn't mounted.. I think it should work that way

---

### Post by drs305 on 2009-05-14
> **luisjeronimo said:**
> I added to sbackup config to not backup if the partition isn't mounted.. I think it should work that way

I don't use sbackup. If that is an switch, option or if the config entry is fairly straightforward (i.e. not a script) I would be happy to mention it in the wiki for others to use. Just provide the details if you'd like.

Thanks in advance.

---

### Post by luisjeronimo on 2009-05-14
Yes it's an option and it's very important for this mistakes not happen.. I have made a screenshot which can help you figure out where to point.

It's on 'Abort backup if destination directory does not exist.'. At destination tab

---

