---
title: "Unable to view all files in Windows NTFS partition"
date: 2008-12-17
forum: General Help
---

### Post by bhavikpatel on 2008-12-17
Hello, 

I have installed Ubuntu on my system recently. I already have Windows Vista on my system. The windows partition is mounted successfully in Ubuntu, but I am not able to view all files in this partition. 

For example, I have a folder named "Movies" in the root of Windows partition, and there are many directories inside "Movies" folder. But I can see very few directories in it. I have already enabled "Shoe hidden files" option, but still I can not see the files. 

The same case is with "Documents and Settings" folder. This folder contains personal files for all users in Windows. But I can not see any folders inside. 

Can you please tell me how to see all files and folders from a Windows partition in Ubuntu? 

Thanks in advance.

---

### Post by linux_tech on 2008-12-17
what is output of 
```
sudo fdisk -l 
```

---

### Post by drs305 on 2008-12-17
It could be a problem with the options mounting the ntfs partition. Folders/files with special characters or spaces in the name - can you detect a pattern on what files you can't see?

You might check your fstab settings to see what locale it is using on mounting. This command will print out the fstab lines containing "ntfs":
```

grep ntfs /etc/fstab

```

I *think* the standard options for a windows mount in the U.S. are (I can't reference a windows machine at the moment). Of course, set it to the locality of the windows setup:
```

defaults,locale=en_US.UTF-8

```

---

### Post by bhavikpatel on 2008-12-17
> **linux_tech said:**
> what is output of 
```
sudo fdisk -l 
```
The output of sudo fdisk -l is: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2813ca74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11870    95342892    7  HPFS/NTFS
/dev/sda2           19211       19457     1984027+  82  Linux swap / Solaris
/dev/sda3           18463       19210     6007825+   7  HPFS/NTFS
/dev/sda4           11871       18462    52950240   83  Linux

---

### Post by bhavikpatel on 2008-12-17
> **drs305 said:**
> It could be a problem with the options mounting the ntfs partition. Folders/files with special characters or spaces in the name - can you detect a pattern on what files you can't see?

You might check your fstab settings to see what locale it is using on mounting. This command will print out the fstab lines containing "ntfs":
```

grep ntfs /etc/fstab

```

I *think* the standard options for a windows mount in the U.S. are (I can't reference a windows machine at the moment). Of course, set it to the locality of the windows setup:
```

defaults,locale=en_US.UTF-8

```
I have seen the content of /etc/fstab file, but it contains entries for only ext3 and swap partitions!!

Then can you tell me how Windows partitions are mounted?

---

### Post by drs305 on 2008-12-17
> **bhavikpatel said:**
> I have seen the content of /etc/fstab file, but it contains entries for only ext3 and swap partitions!!

Then can you tell me how Windows partitions are mounted?

If you want to include it in fstab here are the instructions:

If you already have a mountpoint, skip this step. If you don't, you can name it anything you like but I'll call it *windows*. Steps 2/3 are not necessarily required as ownership of ntfs files is established at mounting.

Items in [COLOR="Red"]red[/COLOR] need to be checked and perhaps changed by you.
```

sudo mkdir /media/[COLOR="Red"]windows[/COLOR]
sudo chown -R *[COLOR="Red"]yourusername[/COLOR]* /media/[COLOR="Red"]windows[/COLOR]
chmod -R 750 /media/[COLOR="Red"]windows[/COLOR]

```

Make a backup and then open fstab for editing:
```

sudo cp /etc/fstab /etc/fstab.12172008
gksudo gedit /etc/fstab

```

Add this line. Change XX to the device number, or better yet, use the UUID in the format of *UUID=XXX-XXXX-XX*:
```

/dev/sdXX /media/[COLOR="Red"]windows[/COLOR] ntfs-3g auto,users,uid=1000,umask=027,[COLOR="Red"]locale=en_US[/COLOR].UTF-8 0 0
or:
UUID=XXXXXX /media/[COLOR="Red"]windows[/COLOR] ntfs-3g auto,users,uid=1000,umask=027,[COLOR="Red"]locale=en_US[/COLOR].UTF-8 0 0

```
Save the file, then:
```

sudo mount -a

```

Your windows partition should now be mounted on /media/windows

---

