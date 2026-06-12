---
title: "DUAL HARD DRIVES, ONE missing?"
date: 2009-01-26
forum: General Help
---

### Post by birdmanJR on 2009-01-26
hey guys, 

i seem to have a problem. i have an HP dv8135nr that is configured with two physical HD's. from what i can see, there is only one drive that intrepid is paying attention to. this was also the case with his older brother heron. i have been using ubuntu since heron and have figured out most things myself along with a little accomplished reading. but so far this hard drive seems to elude me. can anybody help?

terminator fdisk-l output

jr@Birdman:~$ sudo fdisk -l
[sudo] password for jr: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16351635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12161    97683201   83  Linux

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdedc5ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2             121       12161    96719332+   5  Extended
/dev/sdb5             121       11788    93723178+  83  Linux
/dev/sdb6           11789       12161     2996091   82  Linux swap / Solaris
jr@Birdman:~$ 


and here are a few screenshots of computer, gparted

any help would be greatly appreciated




[/B]"Hatred Outlives the Hateful"[/B]

---

### Post by cariboo on 2009-01-26
It looks to me that you have 2 100Gb hard drives.
drive /dev/sda has one partition, and drive two /dev/sdb has 2 extended partitions / and swap. 

It looks like you are booting /dev/sda1. Can you mount /dev/sda1 manually eg:

```
sudo mount /dev/sda1 /mnt
```

JIm

---

### Post by birdmanJR on 2009-01-26
hey jim, thanks for the reply. 

i tried to mount sda1 and this is what i got

jr@Birdman:~$ sudo mount dev/sda1 /mnt
[sudo] password for jr: 
mount: special device dev/sda1 does not exist
jr@Birdman:~$

---

### Post by mb_webguy on 2009-01-26
EDIT: Jim beat me to it.

You should have a / in front of /dev/sda1.   And you should really create a mount point (i.e. directory) under /mnt, rather than using /mnt itself.

---

### Post by birdmanJR on 2009-01-26
ok so i mounted like you said "put / in front of the dev" and terminator did not send back a reply so i guess it took it. now when i go to computer i see a folder thats called mnt. i right click and properties it and it tells me that is 89.6 gb wide. the only file in it is a lost+found. can i rename it or put it somewhere more useful like the computer:///?

---

### Post by mb_webguy on 2009-01-26
If you're talking about renaming or moving "lost+found", then no.  That's a special folder that Linux puts in the topmost directory of each volume, and where it puts files recovered if the drive becomes corrupted.

If you're talking about moving or renaming "mnt", the drive you just mounted, then sure.  That's one of the great things about Linux.  You can put drives anywhere you want in the file system.

Just unmount the drive with the command "umount /mnt" (not that it's "umount", and not "unmount"), then create a folder where you want the drive to be located, such as "/media/music" or "/mnt/mystuff" or "/home/jr/whatever", and then use the mount command again, this time using that directory.

And you should really put an entry in fstab so that it's automatically mounted on startup.

---

### Post by birdmanJR on 2009-01-26
sounds good. any hint on some code that would let me do that?

---

### Post by mb_webguy on 2009-01-26
Sure.  Take a look at these pages...

[How to fstab]("http://ubuntuforums.org/showthread.php?t=283131")
[Fstab: Community Ubuntu Documentation]("https://help.ubuntu.com/community/Fstab")

EDIT:  Here's a quick example.  If you want the ext3 partition /dev/sda1 to be mounted at the location /mnt/mystuff, then you would open fstab with the command "gksu gedit /etc/fstab" and add the following line to the end of the file.```
/dev/sda1 /mnt/mystuff ext3 defaults 0 2
```

---

### Post by louieb on 2009-01-26
Might just check to see what is mounted where. Please post the output of:
```
mount
```

---

### Post by birdmanJR on 2009-01-26
here you go louieb

jr@Birdman:~$ mout
bash: mout: command not found
jr@Birdman:~$ mount
/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jr)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jr)
/dev/sda1 on /mnt type ext3 (rw)
jr@Birdman:~$ 

and thank you very much webguy. i will do some reading on that when i get home today. ive been wanting to learn about fstab.

you guys are great.


"If i were still on windows, this would be a $200 phone call and still nothing would be done"

---

### Post by louieb on 2009-01-26
```

/dev/sdb5 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda1 on /mnt type ext3 (rw)

```Both ext3 partitions listed in your fdisk output are present. 
/dev/sdb5 is your Ubuntu install
/dev/sda1 is your 2nd drive. and the path to is  /mnt  which is odd I wound have expected it to be mounted on a subdirectory inside /media
such as **/media/sdb1**.  or in a subdirectory inside /mnt such as **/mnt/stuff**. 

Look at the links **mb_webguy** gave  think that will get on the right track. 
fun and luck to you too.

---

