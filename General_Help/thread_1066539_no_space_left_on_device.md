---
title: "no space left on device"
date: 2009-02-11
forum: General Help
---

### Post by ojve on 2009-02-11
Hi!

Today I got an error when I tried to open a file from a webpage saying I had no space left on the root partition. This sounded very strange to me but I checked df says there's no space left on the device. I emptied the trash and deleted a couple of gigs worth of .deb files and still the same problem. How do I fix this? 

I think it may havestarted when I connected and disconnected my usb-harddrive yesterday night, but I have no idea how or why.

My hard drive is 320GB divided in four partitions, one each for:
- Windows
- Ubuntu
- Linux swap
- Files and stuff

The partition with all my files is mounted as the /home folder

some output:
$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda2            3204992  411785 2793207   13% /
tmpfs                 505778       3  505775    1% /lib/init/rw
varrun                505778      68  505710    1% /var/run
varlock               505778       2  505776    1% /var/lock
udev                  505778    5144  500634    2% /dev
tmpfs                 505778       2  505776    1% /dev/shm
lrm                   505778      17  505761    1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda4            16080896   37189 16043707    1% /home
/dev/sda1            3191300   78241 3113059    3% /media/sda1
overflow              505778      69  505709    1% /tmp

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G   23G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  224K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G   76K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda4             242G   73G  170G  30% /home
/dev/sda1              25G   22G  3.0G  89% /media/sda1
overflow              1.0M  1.0M     0 100% /tmp

$ sudo du -hc --max-depth=1
48K     ./lost+found
12G     ./var
16M     ./etc
24G     ./media
7.3M    ./bin
63M     ./boot
2.9M    ./dev
73G     ./home
557M    ./lib
4.0K    ./mnt
4.0K    ./opt
du: cannot access `./proc/23304/task/23304/fd/4': No such file or directory
du: cannot access `./proc/23304/task/23304/fdinfo/4': No such file or directory
du: cannot access `./proc/23304/fd/4': No such file or directory
du: cannot access `./proc/23304/fdinfo/4': No such file or directory
0       ./proc
8.4M    ./root
8.1M    ./sbin
4.0K    ./srv
0       ./sys
1.0M    ./tmp
7.9G    ./usr
4.4M    ./lib32
117G    .
117G    total

Any help appreciated

//T

---

### Post by cdtech on 2009-02-11
It would be much easier to read if you paste the output of:
```
sudo fdisk -l
```
and:
```
df -h
```
Within code blocks....

**UPDATE::.**
Do you have any kernel images that your not using? That would kill a lot of space. Have you checked your log files?

---

### Post by ojve on 2009-02-11
Yeah, sorry, I'll use tags next time. 

I could swear that I had rebooted before making that post, but anyway, now it works again, sorry for taking up your time.

Another question though. This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda2 :
UUID=19d6a67c-31bf-4c3b-94a8-a95fcc347612       /       ext2    relatime,errors=remount-ro      0       1
#Entry for /dev/sda4 :
UUID=5a52adce-b84f-4b1b-b9ce-0d52214ba42f       /home   ext3    defaults        0       2
#Entry for /dev/sda1 :
UUID=84F4BC9BF4BC90C2   /media/sda1     ntfs    defaults,nls=utf8,umask=0222    0       0
#Entry for /dev/sda3 :
UUID=db76e968-3d85-46f1-b4c1-5795ac2ac698       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0
```

I still get sda4 mounted in a directory called /media/data as well. Could any one give me a clue why this could be?

Thx
//Thomas

EDIT: and thanks to cdtech for the quick reply!:)

---

### Post by cdtech on 2009-02-11
> Yeah, sorry, I'll use tags next time. 
Not a problem, just easier to read. Posting the output of "mount | column -t" will show all devices that are mounted. If its not listed then its not mounted but rather created. Are you sure you didn't create that directory within the media directory?

---

### Post by drs305 on 2009-02-11
If you run the following you can check your UUIDs to see if they are correct in fstab:
```
sudo blkid -c /dev/null
```

Edited: Just noticed you said it was *also* mounted in /media/data...
```
cat /etc/mtab
``` will also show what is mounted where.

Does the sda4 partition have a label of "data"?

---

### Post by ojve on 2009-02-11
mtab says:
```
thomas@LapTorkel:~$ cat /etc/mtab
/dev/sda2 / ext2 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda4 /home ext3 rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
```

mount gives me:
```
thomas@LapTorkel:~$ mount | column -t
/dev/sda2    on  /                                        type  ext2         (rw,relatime,errors=remount-ro)
tmpfs        on  /lib/init/rw                             type  tmpfs        (rw,nosuid,mode=0755)
/proc        on  /proc                                    type  proc         (rw,noexec,nosuid,nodev)
sysfs        on  /sys                                     type  sysfs        (rw,noexec,nosuid,nodev)
varrun       on  /var/run                                 type  tmpfs        (rw,nosuid,mode=0755)
varlock      on  /var/lock                                type  tmpfs        (rw,noexec,nosuid,nodev,mode=1777)
udev         on  /dev                                     type  tmpfs        (rw,mode=0755)
tmpfs        on  /dev/shm                                 type  tmpfs        (rw,nosuid,nodev)
devpts       on  /dev/pts                                 type  devpts       (rw,noexec,nosuid,gid=5,mode=620)
fusectl      on  /sys/fs/fuse/connections                 type  fusectl      (rw)
lrm          on  /lib/modules/2.6.27-11-generic/volatile  type  tmpfs        (rw,mode=755)
/dev/sda4    on  /home                                    type  ext3         (rw)
/dev/sda1    on  /media/sda1                              type  fuseblk      (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs   on  /sys/kernel/security                     type  securityfs   (rw)
overflow     on  /tmp                                     type  tmpfs        (rw,size=1048576,mode=1777)
binfmt_misc  on  /proc/sys/fs/binfmt_misc                 type  binfmt_misc  (rw,noexec,nosuid,nodev)

```

So apparently, "it" was created, though I have no memory of doing so. What does that even mean? Do I just delete it to get rid of it? I don't really remember if I gave it a label or not but partition manager says it has none.


Thanks for your help
//T

**EDIT:**
Gaah! The error from my original post has just reappeared! it happened after unmounting and disconnecting a USB-stick, and this time I can't seem to get rid of it by just rebooting:```


thomas@LapTorkel:~$ sudo fdisk -l
[sudo] password for thomas:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea99ea99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25600000    7  HPFS/NTFS
/dev/sda2            3188        6375    25600000   83  Linux
/dev/sda3            6375        6897     4194304   82  Linux swap / Solaris
/dev/sda4            6898       38913   257168520   83  Linux

```

```
thomas@LapTorkel:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G   24G     0 100% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  224K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  2.8M  2.0G   1% /dev
tmpfs                 2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda4             242G   74G  169G  31% /home
/dev/sda1              25G   22G  3.0G  89% /media/sda1
overflow              1.0M   32K  992K   4% /tmp

```

there should be at least *some* space available on /dev/sda2 right? Especially since I like I said deleted a lot ofstuff from it.

//T

---

### Post by cdtech on 2009-02-11
> So apparently, "it" was created, though I have no memory of doing so. What does that even mean? Do I just delete it to get rid of it? I don't really remember if I gave it a label or not but partition manager says it has none.
Yes, it would be ok to delete the directory within "/media/data". If it where me I would use the Live CD to do the job: this way your sure the sda device is not mounted. This will also clear up some space on your / (root).

**UPDATE::.**
> /dev/sda4             242G   74G  169G  31% /home
If your home directory is saved within the /media/data directory, then deleting the directory will clean up 74G of space......

---

### Post by ojve on 2009-02-18
Hey again!

Thanks for your help. I decided I didn't need the extra partition, so I smacked my two linux partitions into one and deleted the "created folder" while I was at it.

So far everything seems to work fine, so I'll let this thread rest until something bad happens:P

//T

---

