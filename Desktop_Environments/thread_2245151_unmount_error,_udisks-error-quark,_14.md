---
title: "unmount error, udisks-error-quark, 14"
date: 2014-09-21
forum: Desktop Environments
---

### Post by Eglefino on 2014-09-21
First I have to tell I'm not English and try to do best to make it readeble for you.

Now the problem with my SSD-card. I have the problem for a very long time but had more places on other hdd for the Trusty system. The problems were also before February 2012 the year I started with Ubuntu and say definite goodbey to Windows (after 31-year). After every installation of a new system version, I made a clean install. But everytime the totally system (p.e. Trusty Tahr) changed from place (first hdd) to another hdd without an error message. Everytime Ubuntu was replaced from /dev/sda1 to /dev/sdc5.  (before with Windows it happend with a normal hdd too). My SSD is maybe 4-years old
Now I got an extra problem because my SD-card was not found again (with 64GB digital photos), so I had to call my mount/unmount problem to a forum:mad:.
The first message below is from when I tried to unmount the SSD:
<code>
Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 1: umount: /: device is busy.
        (In some cases useful info about processes that use the device is found by lsof(8) or fuser(1)) 
(udisks-error-quark, 14)</code> 
I had read over the years a lot about other users with the same problems on several Ubuntu/Linux websites but didn't find the totall solution. Today I tried "ntfsck /dev/sda1" where I got the next message.

<code>
root@eglefinoPC:~# ntfsck /dev/sda1
Boot sector: Bad jump.
Boot sector: Bad NTFS magic.
Boot sector: Bytes per sector is 0.
Volume size is set to zero.
file record corrupted at offset 7032972744 (0x1a332a5c8).
Loading $MFT runlist failed. Trying $MFTMirr.
Failed to read file record at offset 8959136302956019712 (0x7c553f0000000000).
Loading $MFTMirr runlist failed too. Aborting.
NTFS signature is missing.
</code>
The told replacements happened now 3 times, so I have not only a 'Ubuntu Trusty Tahr' at /dev/sda1, but also on another internal hard disks drives (hdd). It is a nice idea to learn the working of Ubuntu, but for real I like more silents and save that energy for other places.

So who can help me, before I tell my other Ubuntu-problems; it are not more problems when I worked with Windows:lolflag:

P.S: I don't know how you all get those codes in a special section <code>?

---

### Post by Eglefino on 2014-09-30
After one week there is no comment on my message, strange.....

---

### Post by coffeecat on 2014-09-30
> **Eglefino said:**
> After one week there is no comment on my message, strange.....

If a thread drops off the first page unanswered, which it can after a few hours, it is less likely to be seen. If you don't get an answer after about 1 day, it's quite OK to bring it up to the top by posting the single word "bump". Most members know what that means. Don't bump too often though.

But to your problem: 

> **Eglefino said:**
> The first message below is from when I tried to unmount the SSD:
```

Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 1: umount: /: device is busy.
        (In some cases useful info about processes that use the device is found by lsof(8) or fuser(1)) 

```

That sounds as though you are trying to unmount your root partition, which is not possible. If that is so, it would explain this:

> **Eglefino said:**
> ```

root@eglefinoPC:~# ntfsck /dev/sda1
Boot sector: Bad jump.
Boot sector: Bad NTFS magic.
Boot sector: Bytes per sector is 0.
Volume size is set to zero.
file record corrupted at offset 7032972744 (0x1a332a5c8).
Loading $MFT runlist failed. Trying $MFTMirr.
Failed to read file record at offset 8959136302956019712 (0x7c553f0000000000).
Loading $MFTMirr runlist failed too. Aborting.
NTFS signature is missing.

```

Your root partition would be ext3 or ext4, so running ntfsck will inevitably cause an error.

Let's see what your setup is like. Post the output of these commands:

```
mount
cat /etc/fstab
sudo fdisk -lu
sudo blkid
```

By the way, the BBCode code tags for terminal output are [noparse]```
 and 
```[/noparse], not <code> and </code> which are html tags. You can't use html in forum posts, for obvious reasons, so please post your terminal output between the BBCode code tags for formatting.

---

### Post by Eglefino on 2014-10-09
> **coffeecat said:**
> If a thread drops off the first page  unanswered, which it can after a few hours, it is less likely to be  seen. If you don't get an answer after about 1 day, it's quite OK to  bring it up to the top by posting the single word "bump". Most members  know what that means. Don't bump too often though. 

The "bump" story I don't understand, where do I have to write the text  'bump', is 'bump' the thread-tittle without writing the real title?
> 
But to your problem: 

That sounds as though you are trying to unmount your root partition,  which is not possible. If that is so, it would explain this:

Your root partition would be ext3 or ext4, so running ntfsck will inevitably cause an error.

As you buy a diskdrive/hdd it's formatted for Windows and read in the  Ubuntu history, that's no problem (it's sometimes better as ext4), so I  let it ' ntfs' and made two partitions
with ext4, it booted normal, so there where no problems at the first few  years. The output from the below commands I will place that in my  comment below
> 

Let's see what your setup is like. Post the output of these commands:

```
mount
cat /etc/fstab
sudo fdisk -lu
sudo blkid
```

By the way, the BBCode code tags for terminal output are [noparse]```
  and 
```[/noparse], not <code> and </code> which are  html tags. You can't use html in forum posts, for obvious reasons, so  please post your terminal output between the BBCode code tags for  formatting.

Thanks Cat, for helping me.

As you can see I' m using the live-CD/DVD now (burned today a new  AMD64.ISO), It wasn' t possible to run Ubuntu because it has crashed  (the with lext during start-up, with errors about plymouth).
During this anwer came I tried to use ' ***fsck**'* :
```

eglefino@eglefinoPC:~$ fsck -A -V
'fsck' uit util-linux 2.20.1
Alle bestandssystemen worden gecontroleerd.
[/sbin/fsck.ext4 (1) -- /mnt/06b96c17-bb4d-494e-8e79-9b2a47fde3b4] fsck.ext4 /dev/sda1 
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda1 is mounted.
e2fsck: Kan niet doorgaan.  Gestopt. [translation, could not finish. Stoped]

```

Than I seared the internet (in Ubuntu-fora) to threads of re-write a MBR  at my SSD (with Grub it was too dicey, because my experience with  Ubuntu is not high), I've tried a lot but every time it stopt or I  couldn't further. I tried it also with Gparted. This morning I installed  "***Testdisk***" from where I could install a new  MBR at /dev/sda, it said it should be okay after a reboot....  I had the  new ISO burned and would install with new energy Trusty Tahr desktop,  but this time there came another error (not seen before):

```
**ubi-partman** failed with exitcode 141. Further information maybe found in
/var/log/syslog. Do you want to try running this step again before continuing? If
you do not, your installation may fail entirely or may be broken.

```
I could not choose something because it was crashed again. So I reset  the PC and started this live-CD again, to comment this reaction, now the  output of "Coffecat's" reaction:

```

ubuntu@ubuntu:~$ mount
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdf1 on /media/ubuntu/9016-4EF8 type vfat  (ro,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdd1 on /media/ubuntu/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
ubuntu@ubuntu:~$ cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb7 swap swap defaults 0 0
/dev/sdc6 swap swap defaults 0 0
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000256f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      702463      350208    b  W95 FAT32
/dev/sda2          702464    55803903    27550720   83  Linux
/dev/sda3        55803904    98557951    21377024   83  Linux
/dev/sda4        98557952   117229567     9335808    f  W95 Ext'd (LBA)
/dev/sda5       116944896   117139455       97280    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07003438

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          208845   140841854    70316505    7  HPFS/NTFS/exFAT
/dev/sdb3       140841855  1047180959   453169552+   7  HPFS/NTFS/exFAT
/dev/sdb4      1047181021  1953520064   453169522    5  Extended
/dev/sdb5      1047181023  1086251039    19535008+  83  Linux
/dev/sdb6      1086251103  1933036259   423392578+  83  Linux
/dev/sdb7      1933037253  1953520064    10241406   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4e06802

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    74235903    37116928    7  HPFS/NTFS/exFAT
/dev/sdc2        74237950  1953523711   939642881    5  Extended
/dev/sdc5        74237952   300443647   113102848   83  Linux
/dev/sdc6      1928382464  1953523711    12570624   82  Linux swap / Solaris
/dev/sdc7       300445696   521844735   110699520   83  Linux
/dev/sdc8       521846784  1928380415   703266816   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00042ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1953458175   976728064    7  HPFS/NTFS/exFAT

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd353a9ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1             256     4980735     2490240   fd  Linux raid autodetect
/dev/sdh3         9437184  3907015007  1948788912    f  W95 Ext'd (LBA)
/dev/sdh5         9453280  3088539647  1539543184   fd  Linux raid autodetect

Disk /dev/sdf: 32.1 GB, 32093765632 bytes
255 heads, 63 sectors/track, 3901 cylinders, total 62683136 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            8192    62683135    31337472    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3826-8FE3" TYPE="vfat" 
/dev/sda2: LABEL="SSD-sda1" UUID="06b96c17-bb4d-494e-8e79-9b2a47fde3b4" TYPE="ext4" 
/dev/sda3: LABEL="ssd-sda2" UUID="d082bda6-0092-4adc-9c93-ef8408b04ce8" TYPE="ext4" 
/dev/sda5: UUID="3829-E8F0" TYPE="vfat" 
/dev/sdb1: LABEL="Door systeem gereserveerd" UUID="A812206D122042A4" TYPE="ntfs" 
/dev/sdb2: LABEL="Station" UUID="D07CD9EA7CD9CB7C" TYPE="ntfs" 
/dev/sdb3: UUID="28724033724007D0" TYPE="ntfs" 
/dev/sdb5: UUID="85b3c951-2d3e-49d7-b01d-0a40ededb3ae" TYPE="ext4" 
/dev/sdb6: UUID="d4131f04-6764-4cdb-a236-fba9152be8a3" TYPE="ext4" 
/dev/sdb7: UUID="80ec169f-deb9-45fc-9dbb-483333a93121" TYPE="swap" 
/dev/sdc1: LABEL="Data" UUID="689274A492747900" TYPE="ntfs" 
/dev/sdc5: UUID="959d3cfc-013f-4533-9f0f-f491b62393b5" TYPE="ext4" 
/dev/sdc6: UUID="e9117e05-d594-436b-86e0-e784b012d568" TYPE="swap" 
/dev/sdc7: LABEL="nieuwe home" UUID="3e3502a2-f385-4730-9667-69ddf055e633" TYPE="ext4" 
/dev/sdc8: LABEL="opslag" UUID="9b94acb2-6436-4e8b-b26a-8a71bdcc6202" TYPE="ext4" 
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660" 
/dev/sdd1: LABEL="My Passport" UUID="8A2CF4F62CF4DE5F" TYPE="ntfs" 
/dev/sdh1: UUID="2e5f3acf-83a0-ea56-3017-a5a8c86610be" TYPE="linux_raid_member" 
/dev/sdh5: UUID="a771354f-4f5a-46da-91f2-7e2fc0a178ee" TYPE="ext4" 
/dev/sdf1: UUID="9016-4EF8" TYPE="vfat" 
ubuntu@ubuntu:~$ 

```
So as you can see/read I have several Ubuntu-installations on my  computer, I controlled this morning al my Ubuntu-installations and from  those installations the files
"initrd.img" and "vmlinuz" (symlinks). Why that is maybe somebody from  here can explain that. It can be of course one of the reason an Ubuntu  installation is not running well.

I tell it everytime again, I do my best to get a good English  translation, because I learned that English 43-years ago, so read  between the lines if you can' t understand :wink:.

Thanks for helping.

---

### Post by coffeecat on 2014-10-09
> **Eglefino said:**
> The "bump" story I don't understand, where do I have to write the text  'bump', is 'bump' the thread-tittle without writing the real title?

I explained in my earlier post. If you want to bring your thread up to the top, simply post the single word "bump" in a new post. Bump stands for "bring up my post".

> **Eglefino said:**
> 
As you buy a diskdrive/hdd it's formatted for Windows and read in the  Ubuntu history, that's no problem (it's sometimes better as ext4), so I  let it ' ntfs' and made two partitions
with ext4, it booted normal, so there where no problems at the first few  years. The output from the below commands I will place that in my  comment below

Indeed, but I think you missed the point I made in my earlier post. You were trying to run ntfsfix on your Ubuntu root partition which won't work. It's a common mistake - you just need to be sure that you're trying to repair the correct partition, and that the partition you are trying to repair is not mounted. 

> **Eglefino said:**
> This morning I installed  "***Testdisk***" from where I could install a new  MBR at /dev/sda, 

That is not the purpose of testdisk. Testdisk is for recovering lost partitions.

> **Eglefino said:**
> now the  output of "Coffecat's" reaction:

The output of mount and cat /etc/fstab from the live DVD session tell us nothing of use. We need those outputs from the problem system, but I understand that you can't boot into that system now. The output of the later two commands show a rather complex partition layout. If I am reading you correctly, your problem has changed in that you have several operating systems on that one hard drive and are unable to boot into them. Am I correct?

If so, I suggest the following.

Have a look at this community page:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Run boot-repair either by installing it to a live Ubuntu session, or by using the boot-repair-disk as described on that page. Create a boot info summary and take a note of your boot info URL. Decide which of the installed operating systems you wish to boot into and start a new thread, describing what you wish to achieve and posting a link to your boot info URL. You'll be better off with a new thread - you will get more and swifter responses.

Or it may be that an attempted repair from the boot-repair app will achieve what you need.

---

