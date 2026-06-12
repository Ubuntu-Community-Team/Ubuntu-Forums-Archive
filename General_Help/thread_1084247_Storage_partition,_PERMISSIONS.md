---
title: "Storage partition, PERMISSIONS"
date: 2009-03-01
forum: General Help
---

### Post by justin_c18 on 2009-03-01
All even I've tried to setup proper partitions for my storage partition that will serve my dual boot laptop. The partition is on the same drive I dual boot with. I can't seem to get figure out how to get permission to allow user(with root) to get read/write/execute enabled.

I only want the user and root to have full permissions on the partition. I don't want others to read/write/execute within it.

/etc/fstab is

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 /               ext3    relatime,erro$
# /dev/sda1
UUID=857cd650-3fcc-4cf8-8b50-4bbbdaee26a2 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/Storage ext3 defaults 1 0


```

What would be nice is to have a group enabled for both user and root to enable what I want so no one else can see or use/ copy/ paste into it.

stat /dev/sda4 reads:

```

  File: `/dev/sda4'
  Size: 0         	Blocks: 0          IO Block: 4096   block special file
Device: eh/14d	Inode: 5868        Links: 1     Device type: 8,4
Access: (0660/brw-rw----)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2009-03-01 16:52:45.581941674 -0500
Modify: 2009-03-01 16:52:31.704004813 -0500
Change: 2009-03-01 20:39:54.453941665 -0500

```

stat /media/Storage reads:

```

  File: `/media/Storage/'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 804h/2052d	Inode: 2           Links: 4
Access: (0007/d------rwx)  Uid: (  755/ UNKNOWN)   Gid: ( 1000/  justin)
Access: 2009-03-01 16:49:15.000000000 -0500
Modify: 2009-03-01 16:05:32.000000000 -0500
Change: 2009-03-01 16:49:15.000000000 -0500

```

Basically when I formatted the drive, I 'sudo mkdir /dev/sda4 /media/Storage'. Not sure if is messing anything up.

It's obvious I need help. and all the help I get is much appreciate.

Thank you in advance.
Justin

---

### Post by taurus on 2009-03-01
First, I would edit /etc/fstab and change the entry for /dev/sda4 from what you have right now to this.

```
/dev/sda4 /media/Storage ext3 defaults **[COLOR="Blue"]0 2[/COLOR]**
```
Now, if you want to write to /media/Storage without root privilege, just change the ownership of /media/Storage from root to your login name, _assuming_ your login name is justin.

```
sudo chown -R justin:justin /media/Storage
sudo chmod 700 /media/Storage
ls -la /media
```
Now, only user justin and root can read or write to /media/Storage.  Nobody else can even take a peak it there.

---

### Post by justin_c18 on 2009-03-01
> **taurus said:**
> First, I would edit /etc/fstab and change the entry for /dev/sda4 from what you have right now to this.

```
/dev/sda4 /media/Storage ext3 defaults **[COLOR="Blue"]0 2[/COLOR]**
```
Now, if you want to write to /media/Storage without root privilege, just change the ownership of /media/Storage from root to your login name, _assuming_ your login name is justin.

```
sudo chown -R justin:justin /media/Storage
sudo chmod 700 /media/Storage
ls -la /media
```
Now, only user justin and root can read or write to /media/Storage.  Nobody else can even take a peak it there.

First off, thank you very much for that. I've been looking to do that same thing all day. And, it was obviously in to those two last numbers you told me to change. 

ls -la /media shows

```

drwx------  5 justin justin 4096 2009-03-01 22:41 Storage

```

For a better explanation, what did the [COLOR="Navy"]0 2[/COLOR] do? 

And second, when I create a folders, or files, right click in nautilus, properties, and permissions - the said files don't retain the same permissions as the Storage permission. Does that make sense, and does it matter? Can I change the permissions to be the same as the partition permissions once created, or moved into the partition?

Thanks very much
Justin

---

### Post by soapwater on 2009-03-02
HI Guys, I'm a new Ubuntu user (one week now and I like it a lot) but I have also a problem with permissions for my FAT32-drive that I share with WindowsXP.
I managed to mount the disk automatically and changed /etc/fstab. Than I tried the command
 ```
sudo chown -R justin:justin /media/Storage
```

But I only get messages like 'operation not permitted' for every file on the disk... When using ```
ls -la /media
```, I see that only root has the right privileges to write

---

### Post by soapwater on 2009-03-02
Whoop, and now I don't have permission anymore do view the files, to mount or unmount... How to fix this?

---

### Post by taurus on 2009-03-02
> **soapwater said:**
> HI Guys, I'm a new Ubuntu user (one week now and I like it a lot) but I have also a problem with permissions for my FAT32-drive that I share with WindowsXP.
I managed to mount the disk automatically and changed /etc/fstab. Than I tried the command
 ```
sudo chown -R justin:justin /media/Storage
```

But I only get messages like 'operation not permitted' for every file on the disk... When using ```
ls -la /media
```, I see that only root has the right privileges to write

> **soapwater said:**
> Whoop, and now I don't have permission anymore do view the files, to mount or unmount... How to fix this?

How did you mount your fat32/vfat partition through /etc/fstab?  Remember, fat32/vfat doesn't play well with permissions/ownership stuff so chmod/chown doesn't do any good.

Post the output of these commands from a terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by taurus on 2009-03-02
> **justin_c18 said:**
> 

```

**drwx**------  5 justin justin 4096 2009-03-01 22:41 Storage

```


Once you've set the permissions for /media/Storage to 700, it doesn't matter what kind of permissions you have for files and directories under it, nobody is able to view them.

Just log in as another user and see what happens when you run this command from a terminal.

```
cd /media/Storage
-or-
ls -la /media/Storage
```

---

### Post by justin_c18 on 2009-03-02
I don't like hijacked posts because not only did it not answer all the proceeding questions, but different filesystems are different. :mad:

Write and ask in your own post for more clarity. :(

---

### Post by justin_c18 on 2009-03-02
So, now whenever I restart the computer, permissions to the files and folders inside my Storage partition are not correct. My permissions are gone, and I can't edit the folder, or anything inside it.

How can I fix it so justin and root have permission over the folers and files? I can't go into properties in nautilus and change the permissions, but that's not what I want.

Thanks.

---

### Post by taurus on 2009-03-02
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
ls -la /media
df -h
```

---

### Post by justin_c18 on 2009-03-02
> **taurus said:**
> Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
ls -la /media
df -h
```

Actually, the folders must hvae been there when you told me to change permissions around because I just logged out, then in, new folder permissions stayed the same, then restarted, and the folders stayed the same. My error, sorry.

But, just for more clarity:

sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cd6e240

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2   *         132        3567    27599670   83  Linux
/dev/sda3            3568        7003    27599670   83  Linux
/dev/sda4            7004        9729    21896595   83  Linux

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=857cd650-3fcc-4cf8-8b50-4bbbdaee26a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/Storage ext3 defaults 0 2
/dev/sda3 /media/Jaunty ext3 defaults 0 2

```

ls -la /media
```

drwxr-xr-x  5 root   root   4096 2009-03-02 10:13 .
drwxr-xr-x 21 root   root   4096 2009-03-02 09:35 ..
lrwxrwxrwx  1 root   root      6 2009-02-27 15:41 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2009-02-27 15:41 cdrom0
-rw-r--r--  1 root   root      0 2009-03-02 10:13 .hal-mtab
drwxr-xr-x 21 root   root   4096 2009-03-01 12:32 Jaunty
drwx------  6 justin justin 4096 2009-03-02 10:05 Storage

```

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              27G  3.4G   22G  14% /
varrun               1009M  108K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   56K 1009M   1% /dev
devshm               1009M   44K 1009M   1% /dev/shm
lrm                  1009M   39M  971M   4% /lib/modules/2.6.24-23-generic/volatile
/dev/sda4              21G  173M   20G   1% /media/Storage
/dev/sda3              26G  2.1G   23G   9% /media/Jaunty
gvfs-fuse-daemon       27G  3.4G   22G  14% /home/justin/.gvfs

```

Thanks a lot.

---

### Post by taurus on 2009-03-02
So, can you save or remove anything in /media/Storage?

```
touch /media/Storage/testing
ls -la /media/Storage
rm /media/Storage/testing
ls -la /media/Storage
```

---

### Post by justin_c18 on 2009-03-02
> **taurus said:**
> So, can you save or remove anything in /media/Storage?

```
touch /media/Storage/testing
ls -la /media/Storage
rm /media/Storage/testing
ls -la /media/Storage
```

touch /media/Storage/testing works

ls -la /media/Storage outputs:
```

total 24
drwx------ 6 justin justin 4096 2009-03-02 10:46 .
drwxr-xr-x 5 root   root   4096 2009-03-02 10:13 ..
drwx------ 2 root   root   4096 2009-03-02 09:58 lost+found
-rw-r--r-- 1 justin justin    0 2009-03-02 10:46 testing
d------rwx 4 justin justin 4096 2009-03-01 13:47 .Trash-1000
drwxrwx--- 2 justin justin 4096 2009-03-01 16:05 untitled folder
drwxr-xr-x 2 justin justin 4096 2009-03-02 10:05 untitled folder 2

```

rm /media/Storage/testing works
ls -la /media/Storage doesn't show testing anymore. :)

It's working perfect. Thanks a lot. 
With that said, and done. Now, I'm reading how to encrypt the partition. It shall be fun, I need to get a USB thumb drive to put my keys on first, reading a bit first helps. :)

Thanks a lot.
Have a good day/night.
Justin.

---

### Post by sparvik on 2009-03-11
I have a problem with permissions as well.

I took my external HDD and repartitioned it.  I left the NTFS partition on there and and just shrunk it enough to add an ext3 partition large enough for my ubuntu.  I still have the dual boot setup on my internal hdd so I boot into ubuntu and tried to copy files over. No paste option is available.  

That was when I opened properties on that drive and the permissions say:
"the permissions of "disk-1" could not be determined"

I am trying to figure this out before my internal HDD dies for good.

---

### Post by taurus on 2009-03-11
> **sparvik said:**
> I have a problem with permissions as well.

I took my external HDD and repartitioned it.  I left the NTFS partition on there and and just shrunk it enough to add an ext3 partition large enough for my ubuntu.  I still have the dual boot setup on my internal hdd so I boot into ubuntu and tried to copy files over. No paste option is available.  

That was when I opened properties on that drive and the permissions say:
"the permissions of "disk-1" could not be determined"

I am trying to figure this out before my internal HDD dies for good.

Are you mounting your external through /etc/fstab?

Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

