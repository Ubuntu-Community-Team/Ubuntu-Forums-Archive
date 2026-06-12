---
title: "mount a windows ntfs drive in ubuntu"
date: 2009-05-22
forum: General Help
---

### Post by miocene on 2009-05-22
I've successfully installed ubuntu on my dell xps 410 and all is working ok.
Now I want to mount my windows drive so I can access my files...

Ubuntu is installed on a seperate HD to Windows. Windows is installed on a 160GB RAID 0 array. Here is the fdisk output from terminal:

```
root@harry-desktop:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       38904   312390656    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000064

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d037

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9151    73505376   83  Linux
/dev/sdc2            9152        9546     3172837+   5  Extended
/dev/sdc5            9152        9546     3172806   82  Linux swap / Solaris
```


Is it possible to mount my drive? Please bear in mind I'm a bit of a noob.

---

### Post by taurus on 2009-05-22
Install ntfs-config and see if it can configure those two ntfs partitions so they would be mounted automatically each time you boot.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by miocene on 2009-05-22
I've installed ntfs-config but all it does is ask me if I want to enable write-support on an external device.

My windows drive is not visible anywhere...

---

### Post by KhurramM on 2009-05-22
Show the output of:

cat /proc/partitions

cat /proc/mounts

sudo /sbin/fdisk -l

---

### Post by taurus on 2009-05-22
Wubi?

---

### Post by miocene on 2009-05-23
Cheers for the reply.
Ok here's the ouputs:

```
harry@harry-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  156250000 sda
   8        1     102400 sda1
   8        2  156146576 sda2
   8       16  156250000 sdb
   8       32   76678245 sdc
   8       33   73505376 sdc1
   8       34          1 sdc2
   8       37    3172806 sdc5
   8       48    3964416 sdd
```


```
harry@harry-desktop:~$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
/dev/disk/by-uuid/f6d85ace-94eb-480d-880c-16268d533e3e / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/harry/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1000 0 0
/dev/sdd /media/disk vfat rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush 0 0
/dev/sr0 /media/cdrom0 udf ro,nosuid,nodev,utf8 0 0
```

and...

```
harry@harry-desktop:~$ sudo /sbin/fdisk -l 
[sudo] password for harry: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       38904   312390656    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000064

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d037

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9151    73505376   83  Linux
/dev/sdc2            9152        9546     3172837+   5  Extended
/dev/sdc5            9152        9546     3172806   82  Linux swap / Solaris

Disk /dev/sdd: 4059 MB, 4059561984 bytes
125 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?      100405      247697   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(100404, 79, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(247696, 24, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?       21767      271577   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(21766, 48, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(271576, 60, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      241276      491086   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(241275, 3, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(491085, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?      372346      372354       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(372345, 119, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(372353, 14, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


```

---

### Post by DeMus on 2009-05-23
> **miocene said:**
> I've installed ntfs-config but all it does is ask me if I want to enable write-support on an external device.

My windows drive is not visible anywhere...

Could it be the drives are mounted already? Open Nautilus (Places - home folder) and look in the left column if you see your windows drives there.

---

### Post by QIII on 2009-05-23
DeMus is on to something there.

But what you may see is something like "500 GB Media" (Depending on the size of the disk or partition).

If you see something like that, take a look at it and see if it is your Windows disk or partition.

---

### Post by ronparent on 2009-05-23
I'm sorry I missed your initial post, it might have saved some time. It appears you have two drives probably setup in a raid0 array - sda and sdb. Presuming you have a MB raid controller you would be using a 'fakeraid'. Don't let the term throw you. To see it in ubuntu you need open a terminal and run:

**sudo apt-get install dmraid -y**

then if the install was successful continue with
[B]
sudo dmraid -ay[/B]

At this point you will see the results in /dev/mapper. I myself am stuck with the next step to mount the raid partitions automatically in ubuntu 9.04. In 8.10 I merely edited the /dev/fstab as sudo to link the symbolic links you see in /dev/mapper automatically to mount points created for that purpose. If you are using 8.10 I can tell you how to do this. If it is 9.04, I am still trying to figure that out! At this point you can do it manually with a mount command:

**mount /dev/mapper/<your raid partition entry> /media/<whatever you want to call it>**

It can do no harm to try it and see if it works.

---

### Post by miocene on 2009-05-23
OK thanks I installed dmraid but don't know what my raid partition entry is.
How do I find out what it is?

---

### Post by ronparent on 2009-05-23
If you have installed and run dmraid -ay, then you see the raid drive and the individual partitions in /dev/mapper/. These appear as files with 0 length. They are actually symbolic links to the raid partions (they have a name with 1, 2, etc appended to the array name).

You haven't mentioned yet what version ubuntu you are using. In either case you can use the mount command I illustrated to manually mount them.

---

### Post by ronparent on 2009-05-23
On second thought, try **dmraid -r**. This will discover any functioning raid arrays on your system. Also all the commands I gave you must be run as sudo.

---

### Post by miocene on 2009-05-25
Ok I got this:

```
harry@harry-desktop:~$ sudo dmraid -r
/dev/sdb: isw, "isw_bgdjcgdacf", GROUP, ok, 312499998 sectors, data@ 0
/dev/sda: isw, "isw_bgdjcgdacf", GROUP, ok, 312499998 sectors, data@ 0

```and this:
```

harry@harry-desktop:~$ sudo dmraid -ay
[sudo] password for harry: 
RAID set "isw_bgdjcgdacf_ARRAY" already active
RAID set "isw_bgdjcgdacf_ARRAY1" already active
RAID set "isw_bgdjcgdacf_ARRAY2" already active

```

Does this mean I use sda or sdb as the array name in the command

(I'm using 9.04 btw so I'd start off by trying to get the manual command to work)

**edit**

I tried both and got this
```

harry@harry-desktop:~$ sudo mount /dev/mapper/sda /media/windisk
mount: special device /dev/mapper/sda does not exist

harry@harry-desktop:~$ sudo mount dev/mapper/sdb /media/windisk
mount: special device dev/mapper/sdb does not exist

```

---

### Post by ronparent on 2009-05-25
Use the names in /dev/mapper for each partition present (ignoring the first one with not ending with a number - that is your entire drive and doesn't contain a file system to mount). So in effect you are mounting symbolic links (ie /dev/mapper/nvidia_abcdevice1) from /dev/mapper to your mount point.

---

