---
title: "Can't access /home drive"
date: 2010-04-20
forum: Desktop Environments
---

### Post by gandalf2000 on 2010-04-20
I upgraded to Lucid a few days ago and took the opportunity to partition my /home on a different disk to the OS.  I partitioned the 1Tb into 1 swap partition and 1 extended partition with /home in a partition in that.  After the upgrade I still had /home in the OS partition and the computer can't find the 1Tb drive.  If I run Gparted it shows all the drives and partitions as they are supposed to be.  Please tell me what I have done wrong or what I haven't done right.  Thanks

---

### Post by carl4926 on 2010-04-20
This 1TB drive. Is it a internal sata?

---

### Post by Jimmyfj on 2010-04-20
It seems as if you forgot to set yourself as the owner of the 1TB drive in the new install?

```
sudo chown -R USERNAME:USERNAME /dev/sd1 
```

(or sda, sdb, or sdc) depending on the position of your drive on the bus.

---

### Post by mcduck on 2010-04-20
If you did a fresh install of Lucid, did you remember to set your new home partitions mount point to /home in the installer?

..and if you just did an upgrade, new partitions aren't detected automatically and you have to configure /etc/fstab to mount your new partition into /home manually (and of course copy all the existing home directories to new partition as well).

Could you run "sudo fdisk -l" and "mount" & post the results here so we can have a better look at your drives & partitions and where they are mounted?

---

### Post by gandalf2000 on 2010-04-21
Ok, it is an internal drive and I ran the code from jimmyfj and there was no output from that to post so I next ran the code from mcduck and here is the result:-

bob@gandalf:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8002b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    b  W95 FAT32

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a457b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      120871   970896276    5  Extended
/dev/sdc2          120872      121601     5863725   82  Linux swap / Solaris
/dev/sdc5               1      120871   970896244+  83  Linux

Disk /dev/sdb: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9732    78172258+   7  HPFS/NTFS

Disk /dev/sdh: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db2a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh2               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdh5   *           2       30401   244187968+   b  W95 FAT32
bob@gandalf:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bob)
/dev/sdh5 on /media/49BC-5700 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
bob@gandalf:~$

I still don't have access to the /home partition.  I have also gone back to Karmic and still have the same problem, all this code is from the fresh Karmic install.

---

### Post by carl4926 on 2010-04-21
What is result of

```
cat /etc/fstab
```

---

### Post by gandalf2000 on 2010-04-21
bob@gandalf:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f4fe8f4f-9153-44bd-9b91-0f948abe476c /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=7abf0f61-6379-47b8-ba0e-54038315c5b5 /home           ext3    defaults        0       2
# swap was on /dev/sdc2 during installation
UUID=dc6f9fcd-9cc9-424e-a950-6c448d8b5805 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
bob@gandalf:~$

---

### Post by mcduck on 2010-04-21
Well, based on all that information your /home is on it's own partition (sdc5) on the 1TB drive (sdc) and is working just fine.

What makes you think something is wrong? Do you get any errors when trying to access your home directory, if you do then please post here the errors. Or describe whatever problem you are having with the /home.

---

### Post by gandalf2000 on 2010-04-21
I thought that because I have a home folder on the installation partition and anything saved goes to that, that the home partition was not working.  Should I just delete the home folder on the install disc?  (Scratching head.)

---

### Post by mcduck on 2010-04-21
> **gandalf2000 said:**
> I thought that because I have a home folder on the installation partition and anything saved goes to that, that the home partition was not working.  Should I just delete the home folder on the install disc?  (Scratching head.)

That can't really be the case, it's not possible that you'd have a /home on the same partition as the root and at the same time have the sdc5 partition mounted into the very same location, /home.

Just to make sure that you are aware of how this works, once you mount a separate home partition into /home it will appear just like if the /home was on the same partition as root. The only difference easily noticeable is that when you look at the available space in your /home you'll see diffeent value than in /.

So you don't get any special /newdisk/home kind of thing like Windows likes to separate disks/partitions into c: and d: drives, if you mount a partition into /home then that's where it will be. All drives and partitions appear under the very same root directory in the directory structure.

edit: Perhaps a better explanation: If you move your home directory into a new partition in Windows, then your home directory is moved into new location (from c:\documents and settings/ to d:\documents and settings", for example). In Linux the new partition is moved where your home is, so the home directory stays in the same location (/home), even though the files go to different disk/partition.

---

### Post by gandalf2000 on 2010-04-21
I just realized how it must be and checked properties of the home folder and it is the 1Tb disk.  I had copied all of the stuff from my backup to it and expected it to still be there and when the disc didn't show up in my computer I thought something was wrong.  Sorry for the trouble guys and thanks for the help.  Guess I just didn't think it would be so easy and smooth.  Now, better get to work copying everything to my new /home folder.......again. :oops:  Guys like you make this forum great.

---

