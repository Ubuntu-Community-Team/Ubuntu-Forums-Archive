---
title: "only 947KB in ONLY /tmp (I got 38GB free)"
date: 2008-01-24
forum: Desktop Environments
---

### Post by little cazy on 2008-01-24
**[size=4][COLOR="Red"]Warning: Information in this thread may be outdated, misleading, and should be used with caution, thanks.[/COLOR]**[/size]

everywhere else on m hard drive has 38GB. But my /tmp doesn't.
this causes my computer to load only two second of video from the internet and makes it so I can't download anything.

How do I fix this?

---

### Post by taurus on 2008-01-24
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by jeffus_il on 2008-01-24
Do you have a separate partition for /tmp?
Could you post the output of ```
df -h 
``` in a terminal.

---

### Post by little cazy on 2008-01-24
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc302c302

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            9590        9964     3012187+   5  Extended
/dev/hda3   *           1        9589    77023611   83  Linux
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris
/dev/hda6            9590        9777     1510047   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by little cazy on 2008-01-24
eyez@Zola:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              73G   32G   39G  46% /
varrun                252M  228K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   24M  228M  10% /lib/modules/2.6.22-14-generic/volatile
overflow              1.0M   60K  964K   6% /tmp

---

### Post by little cazy on 2008-01-24
eyez@Zola:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f987c7d4-f17e-4c58-9b7e-80974ed1ca93 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=23b332cd-759a-4949-a194-598d1133839c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by jeffus_il on 2008-01-24
> **little cazy said:**
> eyez@Zola:~$ df -h
```
 Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              73G   32G   39G  46% /
varrun                252M  228K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   24M  228M  10% /lib/modules/2.6.22-14-generic/volatile
overflow              1.0M   60K  964K   6% /tmp
```

I don't understand the last line "overflow", It seems to be a problem.
Are you running some software that creates a userspace filesystem?

---

### Post by jeffus_il on 2008-01-24
I found this:
> **Overflow File System.** Users with lots of data know that processing data on a local filesystem (such as /tmp) is much faster than attempting to harness a distributed file system. However, when /tmp fills up, your entire system stops working! To fix this problem, design and build an "overflow" filesystem for the power user.  Using the [FUSE Toolkit]("http://fuse.sourceforge.net/"), build a filesystem that stores most files in /tmp until the system is nearly full, and then additional data on a larger (but slower) disk in the [CCL storage pool]("http://www.cse.nd.edu/%7Eccl/operations/storage"). Measure the performance of this filesystem on a selection of workloads that need lots of storage.

here:
[http://cse.nd.edu/~dthain/courses/cse60641/fall2007/ideas.html](http://cse.nd.edu/~dthain/courses/cse60641/fall2007/ideas.html)

---

### Post by jeffus_il on 2008-01-24
It may be connected with fuse.

Are you using a fuse filesystem, fusessh smb, communications with windows, file sharing?

---

### Post by erginemr on 2008-01-24
The bizarre thing is; the line
```
overflow              1.0M   60K  964K   6% /tmp
```
besides the overflow thing, reports the capacity of /tmp directory as 1 MB!!

All other lines are from the file "/etc/mtab". Can you please post what is inside that file, too?
```
cat /etc/mtab
```

---

### Post by jeffus_il on 2008-01-24
Mr Cazy has Myth installed, (apparently,  according to previous posts), I wonder if it does something with userspace file systems. I think the patient may have fallen asleep, he hasn't been around for an hour, the problem is becoming interesting...

---

### Post by jeffus_il on 2008-01-24
There is a package called [mythtvfs-fuse-0.5.0.tar.gz]("http://outflux.net/software/pkgs/mythtvfs-fuse/download/mythtvfs-fuse-0.5.0.tar.gz")
Found it here:
[http://outflux.net/software/pkgs/mythtvfs-fuse/](http://outflux.net/software/pkgs/mythtvfs-fuse/)

The plot thickens.

---

### Post by jeffus_il on 2008-01-24
Without doing too much research, I would hazard a guess that removing the package "mythtvfs" will solve the problem.

[http://packages.ubuntu.com/gutsy/utils/mythtvfs](http://packages.ubuntu.com/gutsy/utils/mythtvfs)

---

### Post by erginemr on 2008-01-25
jeffus_il, I believe you are on the right track. Let's wait for the OP to wake up.;-)

---

### Post by little cazy on 2008-01-25
sorry i gone 4 a while here u go.
```
eyez@Zola:~$ cat /etc/mtab
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```

---

### Post by little cazy on 2008-01-25
no, i don't got it installed, never have

---

### Post by jeffus_il on 2008-01-25
Any other user space file systems? for networking? smb? fuse? Some software you have installed has created a user space file system, "overflow"

---

### Post by little cazy on 2008-01-25
allready got that

---

### Post by little cazy on 2008-01-25
no, no other users or network connects. and from what i can get, the only thing with overflow is 'cron'. which i don't use

---

### Post by little cazy on 2008-01-25
also

---

### Post by little cazy on 2008-01-25
here's something, there's a group name 'fuse' in 'user and groups'

---

### Post by erginemr on 2008-01-26
I don't know what fuse is for, but I also have it in my groups but don't experience this problem.

Anyway, here is your /etc/mtab file:
```
eyez@Zola:~$ cat /etc/mtab
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```
and here is mine:
```
/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/hda5 /media/hda5 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/hdb3 /media/hdb3 fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/hdc /media/cdrom0 iso9660 ro,nosuid,nodev,user=ergin 0 0
```

Given the fact that I have no reference to /tmp folder whatsoever, I would suggest you to first backup your "mtab" file with:
```
sudo cp /etc/mtab /etc/mtab.bak
```
and then, edit the file with:
```
gksu gedit /etc/mtab
```
and remove the line that says:
```
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
```
Save the file, exit and reboot to see if there is any improvement.

---

### Post by little cazy on 2008-01-26
ya, that fix it. i can watch my anime again. thank you

---

### Post by erginemr on 2008-01-26
Well, that is some good news! 
:popcorn:
Take Care & Have Fun!

---

