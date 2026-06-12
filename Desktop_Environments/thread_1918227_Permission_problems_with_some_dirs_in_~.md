---
title: "Permission problems with some dirs in ~/"
date: 2012-01-31
forum: Desktop Environments
---

### Post by Dáire Fagan on 2012-01-31
Everything I download with firefox or google chrome to ~/Downloads has the owner root, and group root. 

This is causing problems running some programs like the                tor browser bundle which needs to create and access files currently in ~/Downloads/tor-browser_en-US. 

Am i correct that I dusf should be the owner of these files I have download, and also the group?

I have noticed that some of the dirs in ~/ are set the same as ~/Downloads, so is there some command I can enter into bash to correct this?

Some of them are symlinks to another partition where I store media!

---

### Post by lovinglinux on 2012-02-01
Are you by any chance running Firefox as root?

---

### Post by ruffEdgz on 2012-02-01
> **lovinglinux said:**
> Are you by any chance running Firefox as root?

i would look at that but what about the hierarchy is for ~/Downloads

If you did the following command
```

ll -d ~/Downloads && ll ~/Downloads

```
What do you get?

Just from what you said in your two posts, I see something like this (I'm just guessing):
---

~/Downloads (rwxr-xr-x  root,root)
 |
 |
 ---- /tor-browser_en-US -> /some/where (rwxrwxrwx  root root)
 |
 |
 ---- ect...

---
Please correct me if I'm wrong.

It does sound like a permission issue but you will have to check who has permission to see/write/execute on those symlinked files. 

If the ~/Downloads directory is inside a users homedir (that isn't root) then I don't see why you would need to have it be owned by root. To just change the ownership of the directory only, use this command:
```

sudo chown <username> <group> ~/Downloads

```
Make sure to replace <username> with a username you want and <group> with the group the user is a part of.

For Example:
```

sudo chown ruff edgz ~/Downloads

```
I am changing the directory ~/Doownloads to be owned by the username 'ruff' and the group 'edgz'.

Here is a good link to learn more about file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Dáire Fagan on 2012-03-08
Firstly sorry for the late reply, I had mail notifications disabled somehow.

> **lovinglinux said:**
> Are you by any chance running Firefox as root?

I am just running it using my applications menu as normal. I think there's a problem with lots of things in my home folder.

> **ruffEdgz said:**
> i would look at that but what about the hierarchy is for ~/Downloads

If you did the following command
```

ll -d ~/Downloads && ll ~/Downloads

```What do you get?

```
dusf@banshee:~$ ll -d ~/Downloads && ll ~/Downloads
lrwxrwxrwx 1 dusf dusf 26 2011-05-22 22:01 /home/dusf/Downloads -> /media/DUMP/dusf/Downloads/
lrwxrwxrwx 1 dusf dusf 26 2011-05-22 22:01 /home/dusf/Downloads -> /media/DUMP/dusf/Downloads/

```

> **ruffEdgz said:**
> Just from what you said in your two posts, I see something like this (I'm just guessing):
---

~/Downloads (rwxr-xr-x  root,root)
 |
 |
 ---- /tor-browser_en-US -> /some/where (rwxrwxrwx  root root)
 |
 |
 ---- ect...

---
Please correct me if I'm wrong.

It does sound like a permission issue but you will have to check who has permission to see/write/execute on those symlinked files. 

If the ~/Downloads directory is inside a users homedir (that isn't root) then I don't see why you would need to have it be owned by root. To just change the ownership of the directory only, use this command:
```

sudo chown <username> <group> ~/Downloads

```Make sure to replace <username> with a username you want and <group> with the group the user is a part of.

For Example:
```

sudo chown ruff edgz ~/Downloads

```I am changing the directory ~/Doownloads to be owned by the username 'ruff' and the group 'edgz'.

Here is a good link to learn more about file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Please note, I am executed a sudo chown dusf.dusf ~/ -R before submitting this reply as sudo chown ruff edgz ~/Downloads is apparently the incorrect syntax.

Should I be concerned about this output?

```
chown: changing ownership of `/home/dusf/.mozilla/firefox/jdyoo6w1.default/minidumps/03fb8e2f-d90b-bebb-633030cc-1722166d.dmp': Input/output error
chown: cannot access `/home/dusf/.gvfs': Permission denied
chown: changing ownership of `/home/dusf/.ICEauthority_old': Input/output error
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
```

I am back to this problem because I am trying to complete a live USB install, from Xubuntu but the following command is giving the following errors:

```
dusf@banshee:/mnt/sdf1$ rsync -r /home/dusf/BT5R2-KDE-32_iso/* .
rsync: recv_generator: mkdir "/mnt/sdf1/casper" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/mnt/sdf1/isolinux" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/mnt/sdf1/preseed" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***
rsync: mkstemp "/mnt/sdf1/.README.diskdefines.Aq4BaG" failed: Permission denied (13)
rsync: mkstemp "/mnt/sdf1/.md5sum.txt.nK2eBj" failed: Permission denied (13)
rsync: mkstemp "/mnt/sdf1/.ubuntu.xKjS1W" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
```

```
dusf@banshee:/mnt/sdf1$ sudo rsync -r /home/dusf/BT5R2-KDE-32_iso/* .
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
```

```
root@banshee:~# rsync -r /home/dusf/BT5R2-KDE-32_iso/* .
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
root@banshee:~# sudo rsync -r /home/dusf/BT5R2-KDE-32_iso/* .
rsync: change_dir "/home/dusf/BT5R2-KDE-32_iso" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
```

I used Furious ISO Mount to mount the ISO file, and it did not give me a choice where to mount it, but that dir has the following permissions:

```
dusf@banshee:/mnt/sdf1$ ll -d ~/BT5R2-KDE-32_iso && ll ~/BT5R2-KDE-32_iso
dr-xr-xr-x 1 root root 2048 2012-03-01 00:21 /home/dusf/BT5R2-KDE-32_iso/
total 27
dr-xr-xr-x  1 root root  2048 2012-03-01 00:21 ./
drwxrwx--- 63 dusf dusf 20480 2012-03-08 16:08 ../
dr-xr-xr-x  1 root root  2048 2012-03-01 00:09 casper/
dr-xr-xr-x  1 root root  2048 2011-03-05 15:43 .disk/
dr-xr-xr-x  1 root root  2048 2011-03-05 15:40 isolinux/
-r--r--r--  1 root root  1284 2012-03-01 00:21 md5sum.txt
dr-xr-xr-x  1 root root  2048 2011-03-05 15:40 preseed/
-r--r--r--  1 root root   198 2011-03-05 15:40 README.diskdefines
-r--r--r--  1 root root     0 2011-03-05 15:43 ubuntu

```

Tried the following:

```
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
dusf@banshee:/mnt/sdf1$ sudo su -
root@banshee:~# sudo chown dusf.dusf ~/BT5R2-KDE-32_iso -R
chown: cannot access `/root/BT5R2-KDE-32_iso': No such file or directory
root@banshee:~# sudo chown dusf.dusf /home/dusf/BT5R2-KDE-32_iso -R
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
root@banshee:~# chown dusf.dusf /home/dusf/BT5R2-KDE-32_iso -R
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
```

Currently trying sudo chown dusf.dusf /media/ -R, but it's going to take awhile.

```
root@banshee:~# sudo chown dusf.dusf ~/BT5R2-KDE-32_iso -R
chown: cannot access `/root/BT5R2-KDE-32_iso': No such file or directory
root@banshee:~# sudo chown dusf.dusf /home/dusf/BT5R2-KDE-32_iso -R
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
root@banshee:~# chown dusf.dusf /home/dusf/BT5R2-KDE-32_iso -R
chown: cannot access `/home/dusf/BT5R2-KDE-32_iso': Permission denied
root@banshee:~# sudo chown dusf.dusf /media/
root@banshee:~# sudo chown dusf.dusf /media/ -R
root@banshee:~# sudo chown dusf.dusf /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32/
root@banshee:~# sudo chown dusf.dusf /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32/ -R
root@banshee:~# exit

```

It's very frustrating!

If relevant the DUMP partition is FAT32.


```
dusf@banshee:/mnt/sdf1$ ll -d ~/Downloads/.transmission/BT5R2-KDE-32/ && ll ~/Downloads/.transmission/BT5R2-KDE-32/
drwxrwxrwx 1 root root 0 2012-03-07 10:11 /home/dusf/Downloads/.transmission/BT5R2-KDE-32//
total 2736953
drwxrwxrwx 1 root root          0 2012-03-07 10:11 ./
drwxrwxrwx 1 root root       4096 2012-03-07 10:40 ../
-rwxrwxrwx 1 root root 2802634752 2012-03-07 10:11 BT5R2-KDE-32.iso*
-rwxrwxrwx 1 root root         51 2012-03-06 21:13 BT5R2-KDE-32.txt*
dusf@banshee:/mnt/sdf1$ ll -d /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32/ & ll /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32/
[1] 6157
drwxrwxrwx 1 root root 0 2012-03-07 10:11 /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32//
total 2736953
drwxrwxrwx 1 root root          0 2012-03-07 10:11 ./
drwxrwxrwx 1 root root       4096 2012-03-07 10:40 ../
-rwxrwxrwx 1 root root 2802634752 2012-03-07 10:11 BT5R2-KDE-32.iso*
-rwxrwxrwx 1 root root         51 2012-03-06 21:13 BT5R2-KDE-32.txt*
[1]+  Done                    ls --color=auto -alF -d /media/DUMP/dusf/Downloads/.transmission/BT5R2-KDE-32/

```

---

### Post by oldos2er on 2012-03-08
> **dusf said:**
> If relevant the DUMP partition is FAT32.


Very relevant. Microsoft file systems, including FAT, FAT32, and NTFS don't understand Linux permissions, so chown won't work on them. Instead you set permissions when the partitions are mounted. See [https://help.ubuntu.com/community/Fstab#fat16_and_fat32](https://help.ubuntu.com/community/Fstab#fat16_and_fat32)

---

### Post by Dáire Fagan on 2012-03-08
Are they not mounted already?

> **fat16 and fat32**

 
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
/dev/sdb1 /media/data2 vfat defaults,user,dmask=027,fmask=137 0 0

Also, is the first for FAT16 and the second for FAT32, or are both for both?

---

### Post by oldos2er on 2012-03-08
Those are just examples. I think "vfat" covers both FAT and FAT32.

---

### Post by Dáire Fagan on 2012-03-09
> **oldos2er said:**
> Those are just examples. I think "vfat" covers both FAT and FAT32.

I do not understand what I need to do with the syntax of those examples, or where to put them, or how to find my UUID, please elaborate.

I have read this problem can be solved by adding (or editing?) a line to /etc/ftab/ with a uid=<my uid> option?

This is my current /etc/fstab/ and DUMP is the FAT32 media storage partition.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=57b7cc02-c00b-49ea-8873-b3918feb9eea /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=47adf8d9-0d98-4d8f-8358-db60391ff3c9 /home           ext4    defaults        0       2
#/dev/sda5       none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults    0    0

```

---

### Post by Morbius1 on 2012-03-09
> This is my current /etc/fstab/ and DUMP is the FAT32 media storage partition.Yet fstab says this:
>  UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults    0    0That is not the UUID of a vfat partition - vfat has a different form. That is the UUID of an ntfs partition however and the line in fstab mounts it as such. In fact it should mount it with r/w/x prermissions to everyone even though it will be owned by root.

What would be very helpful at this point is to find out exactly how your system sees the partitions connected to it. Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
mount
```

---

### Post by Dáire Fagan on 2012-03-09
Apologies, it is NTFS.

> **Morbius1 said:**
> What would be very helpful at this point is to find out exactly how your system sees the partitions connected to it. Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
mount
```

```
dusf@banshee:~$ sudo blkid -c /dev/null
[sudo] password for dusf: 
/dev/sda1: LABEL="WINXP" UUID="71FF83E7669614CE" TYPE="ntfs" 
/dev/sda5: LABEL="UBUNTU" UUID="57b7cc02-c00b-49ea-8873-b3918feb9eea" TYPE="ext4" 
/dev/sda6: LABEL="HOME" UUID="47adf8d9-0d98-4d8f-8358-db60391ff3c9" TYPE="ext4" 
/dev/sda7: LABEL="DUMP" UUID="4442D7A83361F05F" TYPE="ntfs" 
/dev/mapper/cryptswap1: UUID="043f4282-bea6-4840-984c-b496b01f824f" TYPE="swap" 
/dev/sdf1: UUID="7404-F5CC" TYPE="vfat" 
dusf@banshee:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda7 on /media/DUMP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/dusf/.Private on /home/dusf type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=dec16495fa86c409,ecryptfs_fnek_sig=5bc4b8c800542861)
gvfs-fuse-daemon on /home/dusf/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dusf)
/dev/sdf1 on /media/7404-F5CC type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

```

---

### Post by Morbius1 on 2012-03-09
This topic just gets more and more confusing. What is this:
> /home/dusf/.Private on /home/dusf type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=dec16495fa86c409,ecryptfs_fnek_sig=5bc4b8c800542861)
I know very little about encrypting directories but that just doesn't look right. Do you have an encrypted home directory?

---

### Post by Dáire Fagan on 2012-03-09
> **Morbius1 said:**
> I know very little about encrypting directories but that just doesn't look right. Do you have an encrypted home directory?

I have carried my home partition through numerous upgrades and clean  installs over the last several years including an emigration to Xubuntu, so I honestly cannot remember if  it was initially set up encrypted, unless you can tell me how to check?

---

### Post by Morbius1 on 2012-03-09
First, unless the other folks who have responded to your question know about encrypted directories I would wait for someone who does. I am not one of those people.

Second, If i was forced to deal with this situation I would set up a second Downloads folder somewhere outside of your home directory. Since this appears to be a dual boot I would place it in /media/DUMP:

[1] Create another Downloads directory:
```
sudo mkdir /media/DUMP/Downloads
```[2] Point all of your browsers or other applications to that folder not the one in your home folder.

[3] If for some reason these applications wont work unless you own the mounted partition then I would change this following line in fstab:
>  UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults    0    0To this:
```
UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults,uid=1000,windows_names    0    0
```**uid=1000** will make you the owner of the mounted partition.
**windows_names** will prevent you from saving a file with a name that Windows cannot interpret.

Then unmount the ntfs partition:
```
sudo umount /media/DUMP
```Then mount it again with this command:
```
sudo mount -a
```If there are any errors it will let you know. If there are none it will mount the ntfs partition with the new set of options.

---

### Post by Dáire Fagan on 2012-03-09
> **Morbius1 said:**
> First, unless the other folks who have responded to your question know about encrypted directories I would wait for someone who does. I am not one of those people.

Second, If i was forced to deal with this situation I would set up a second Downloads folder somewhere outside of your home directory. Since this appears to be a dual boot I would place it in /media/DUMP:

[1] Create another Downloads directory:
```
sudo mkdir /media/DUMP/Downloads
```[2] Point all of your browsers or other applications to that folder not the one in your home folder.

I created the dir, but as you can see from the output below root is still set for all permissions, just like every other dir and file on /media/DUMP, including /media/DUMP/dusf/Downloads which ~/Downloads is symlinked to.


```
dusf@banshee:~$ mkdir /media/DUMP/Downloads
dusf@banshee:~$ ll -d /media/DUMP/Downloads & ll /media/DUMP/Downloads[1] 2881
drwxrwxrwx 1 root root 0 2012-03-09 13:15 /media/DUMP/Downloads/
total 12
drwxrwxrwx 1 root root     0 2012-03-09 13:15 ./
drwxrwxrwx 1 root root 12288 2012-03-09 13:15 ../
[1]+  Done                    ls --color=auto -alF -d /media/DUMP/Downloads
```> **Morbius1 said:**
> 
[3] If for some reason these applications wont work unless you own the mounted partition then I would change this following line in fstab:
To this:
```
UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults,uid=1000,windows_names    0    0
```uid=1000 will make you the owner of the mounted partition.
windows_names will prevent you from saving a file with a name that Windows cannot interpret.

Nice, and thanks for explaining the arguments. I backed up fstab before editing.

Then unmount the ntfs partition:
```
sudo umount /media/DUMP
```Then mount it again with this command:
```
sudo mount -a
```If there are any errors it will let you know. If there are none it will mount the ntfs partition with the new set of options.[/QUOTE]

Done, and I am now set as the owner but not the group, is this what we want or? Please see the output below.

```
dusf@banshee:~$ ll -d /media/DUMP/Downloads & ll /media/DUMP/Downloads
[1] 3342
drwxrwxrwx 1 dusf root 0 2012-03-09 13:15 /media/DUMP/Downloads/
total 12
drwxrwxrwx 1 dusf root     0 2012-03-09 13:15 ./
drwxrwxrwx 1 dusf root 12288 2012-03-09 13:15 ../
[1]+  Done                    ls --color=auto -alF -d /media/DUMP/Downloads

dusf@banshee:~$ ll -d /media/DUMP/dusf/Downloads & ll /media/DUMP/dusf/Downloads 
[1] 3349
drwxrwxrwx 1 dusf root 45056 2012-03-09 13:00 /media/DUMP/dusf/Downloads/
total 1264148
drwxrwxrwx 1 dusf root      45056 2012-03-09 13:00 ./
drwxrwxrwx 1 dusf root       4096 2012-02-25 15:08 ../
drwxrwxrwx 1 dusf root       4096 2012-01-24 18:30 .azureus/
drwxrwxrwx 1 dusf root          0 2012-03-07 10:11 BT5R2-KDE-32/
-rwxrwxrwx 1 dusf root      24675 2012-01-13 02:16 CoD4.sslf*
-rwxrwxrwx 1 dusf root      12487 2012-01-13 02:16 CoD4.txt*
-rwxrwxrwx 1 dusf root       5014 2012-01-13 02:16 CoD5.txt*
-rwxrwxrwx 1 dusf root      24116 2012-02-02 16:37 debian-live-6.0.3-i386-gnome-desktop.img.list*
-rwxrwxrwx 1 dusf root      17505 2012-02-02 16:37 debian-live-6.0.3-i386-gnome-desktop.img.log*
-rwxrwxrwx 1 dusf root      31414 2012-02-02 16:37 debian-live-6.0.3-i386-gnome-desktop.img.packages*
-rwxrwxrwx 1 dusf root 1115684864 2012-02-03 18:57 debian-live-6.0.3-i386-kde-desktop.img*
drwxrwxrwx 1 dusf root       4096 2012-01-12 18:43 .dnacache/
drwxrwxrwx 1 dusf root          0 2012-01-09 20:01 Download me/
-rwxrwxrwx 1 dusf root          0 2012-02-04 13:05 [kat.ph]eminem.2005.curtain.call.the.hits.2cd.320.torrent*
-rwxrwxrwx 1 dusf root          0 2012-02-04 13:07 [kat.ph]guns.n.roses.greatest.hits.2004.torrent*
-rwxrwxrwx 1 dusf root    8895488 2012-02-10 19:47 mkv2vob.exe*
-rwxrwxrwx 1 dusf root  154223002 2012-02-28 14:35 OOo_3.3.0_Linux_x86_install-deb_en-US.tar.gz*
-rwxrwxrwx 1 dusf root   11455274 2012-02-09 10:16 opera_11.61.1250_i386.deb*
-rwxrwxrwx 1 dusf root     803076 2012-02-28 19:12 PathwaysToWork.pdf*
-rwxrwxrwx 1 dusf root     893694 2012-02-29 08:25 tcd-campus.pdf*
-rwxrwxrwx 1 dusf root     502586 2012-02-29 08:25 tcd-main-campus.pdf*
-rwxrwxrwx 1 dusf root     487424 2012-02-29 08:22 TCD MAP  for invites (2).doc*
-rwxrwxrwx 1 dusf root      47311 2012-02-28 15:37 Trainer_Role.pdf*
drwxrwxrwx 1 dusf root       4096 2012-03-08 23:19 .transmission/
-rwxrwxrwx 1 dusf root    1012645 2012-03-08 20:10 Universal-USB-Installer-1.8.8.6.exe*
drwxrwxrwx 1 dusf root      73728 2012-03-09 11:39 .utorrent/
[1]+  Done                    ls --color=auto -alF -d /media/DUMP/dusf/Downloads

```

---

### Post by Morbius1 on 2012-03-09
It doesn't matter what the group is. It really doesn't matter who the owner is either. Your partition was always mounted with r/w/x/ access to everyone. NTFS partitions mount with inheritance so all subfolders and files will also have r/w/x/ permissions.

If you want the group to also be you then add it to the mount options:
```
 UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults,uid=1000,gid=1000,windows_names    0    0
```Then do the "sudo umount ... " / "sudo mount -a" thing again.

---

### Post by Dáire Fagan on 2012-03-09
> **Morbius1 said:**
> It doesn't matter what the group is. It really doesn't matter who the owner is either. Your partition was always mounted with r/w/x/ access to everyone. NTFS partitions mount with inheritance so all subfolders and files will also have r/w/x/ permissions.

If you want the group to also be you then add it to the mount options:
```
 UUID=4442D7A83361F05F    /media/DUMP    ntfs-3g    defaults,uid=1000,gid=1000,windows_names    0    0
```Then do the "sudo umount ... " / "sudo mount -a" thing again.

Do you not think that would make more sense, is there a reason not to, and it will not affect anything on Windows either way, right?

---

### Post by Morbius1 on 2012-03-09
It should make no difference if you add group membership or not since it's mounting with universal access. 
> and it will not affect anything on Windows either way, right?     Linux uses fuse to mount an NTFS partition to produce a "view" of the partition that gives it the appearance of having Linux ownership and permissions. The whole thing is an illusion since a Windows filesystem in reality has no Linux ownership and permissions "bits". However you mount it and with whatever options you use in Linux it will have no impact on Windows. What you do after you mount it - deleting a Windows system file by mistake - is due entirely upon the part of your computer between the keyboard and the chair.

---

### Post by Dáire Fagan on 2012-03-09
That's all done now and I also learned mount -a remounts all files mentioned in fstab, except those who have noauto in their line, thanks! :)

---

