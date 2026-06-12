---
title: "partionion mounting?"
date: 2009-05-23
forum: General Help
---

### Post by Zom-b on 2009-05-23
is it possible to mount another partition I have on my hdd to access the files on it?

---

### Post by taurus on 2009-05-23
Yes.  What filesystem is it?

---

### Post by florus on 2009-05-23
My windows partition appears under 'Places' as 173.0 GB Media; clicking on it mounts the partition. Linux just treats the partition as another file and all the files on it are read/write accessible.

---

### Post by Zom-b on 2009-05-23
> **taurus said:**
> Yes.  What filesystem is it?

it's just another linux partition 

unfortunatly it isn't in teh places menu

---

### Post by taurus on 2009-05-23
Open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Zom-b on 2009-05-24
> **taurus said:**
> Open a terminal and post the outputs of these commands, running one command at a time.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

yeah, taht didn't seem to work

---

### Post by drs305 on 2009-05-24
> **Zom-b said:**
> yeah, taht didn't seem to work

Did you run each of the commands separately? If so, you will have to explain what didn't work. The commands were to provide information to help determine what your problem is.

---

### Post by Zom-b on 2009-05-24
I don't know, here is the output of each one, I don't see anything that looks like it didn't work but when I finish it nothing seems to have changed

```

zomb@zomb-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51d751d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8172    65641558+  83  Linux
/dev/sda2            8173        9729    12506602+   5  Extended
/dev/sda5            9472        9729     2072353+  82  Linux swap / Solaris
/dev/sda6            8173        9410     9944172   83  Linux
/dev/sda7            9411        9471      489951   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```

zomb@zomb-laptop:~$ sudo blkid
/dev/sda1: UUID="9caaecf2-da76-4d5c-856b-ed5cb609b01f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5b467e54-db65-4adc-9548-0c87c22a2905" 
/dev/sda6: UUID="99c70166-80da-457d-85db-51c97b01ffb3" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="374d5d0e-4a28-49e5-b17d-934072c952a0" 

```

```

zomb@zomb-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=99c70166-80da-457d-85db-51c97b01ffb3 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=374d5d0e-4a28-49e5-b17d-934072c952a0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

zomb@zomb-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.4G  3.8G  5.2G  43% /
tmpfs                 344M     0  344M   0% /lib/init/rw
varrun                344M  228K  343M   1% /var/run
varlock               344M     0  344M   0% /var/lock
udev                  344M  164K  343M   1% /dev
tmpfs                 344M     0  344M   0% /dev/shm
lrm                   344M  2.4M  341M   1% /lib/modules/2.6.28-11-generic/volatile

```

---

### Post by drs305 on 2009-05-24
If it's sda1 you are wanting to mount, make a mountpoint and make yourself the owner:
```

sudo mkdir /media/*mountpoint*
sudo chown -R *yourusername:* /media/*mountpoint*

```

Add this line to your fstab. It assumes it is sda1 that is not showing up:
```

UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f /media/mountpoint ext3 defaults 0 2

```

Unmount and remount with the following. If you don't get any error messages, sda1 is mounted properly.
```


Also you might note that sda5 is designated as a swap partition but isn't being used by anything. You only need one swap partition and fstab is using sda7.
sudo mount /dev/sda1

```

---

### Post by Zom-b on 2009-05-24
> **drs305 said:**
> If it's sda1 you are wanting to mount, make a mountpoint and make yourself the owner:
```

sudo mkdir /media/*mountpoint*
sudo chown -R *yourusername:* /media/*mountpoint*

```

Add this line to your fstab. It assumes it is sda1 that is not showing up:
```

UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f /media/mountpoint ext3 defaults 0 2

```

Unmount and remount with the following. If you don't get any error messages, sda1 is mounted properly.
```


Also you might note that sda5 is designated as a swap partition but isn't being used by anything. You only need one swap partition and fstab is using sda7.
sudo mount /dev/sda1

```

when I do that it gives me:
```

zomb@zomb-laptop:~$ sudo chown -R zomb: /media/mountpoint
zomb@zomb-laptop:~$ UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f /media/mountpoint ext3 defaults 0 2
bash: /media/mountpoint: is a directory
zomb@zomb-laptop:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
zomb@zomb-laptop:~$ 

```

---

### Post by drs305 on 2009-05-24
Ok, I wasn't clear enough. The line below should be added to fstab. Substitute whatever the name of the mountpoint you made for "mountpoint", of course. So if you created a folder called "mydata", it would be "/media/mydata":
> UUID=9caaecf2-da76-4d5c-856b-ed5cb609b01f /media/mountpoint ext3 defaults 0 2


To do this, open fstab for editing and add the line above.
```

gksudo gedit /etc/fstab

```
Save and close the file, then run the "sudo mount /dev/sda1" command.

---

### Post by Zom-b on 2009-05-24
> **drs305 said:**
> Ok, I wasn't clear enough. The line below should be added to fstab. Substitute whatever the name of the mountpoint you made for "mountpoint", of course. So if you created a folder called "mydata", it would be "/media/mydata":


To do this, open fstab for editing and add the line above.
```

gksudo gedit /etc/fstab

```
Save and close the file, then run the "sudo mount /dev/sda1" command.

sorry I'm a little dense about things sometimes, alright, it worked, mounted my other partition and is accessible and everything, but when I mounted it it said

```

zomb@zomb-laptop:~$ sudo mount /dev/sda1
[mntent]: line 14 in /etc/fstab is bad

```

---

### Post by drs305 on 2009-05-24
That is probably the line you added. You can open gedit and go directly to the bad line with this command:
```

gksudo gedit +14 /etc/fstab

```

You can post it or if it is slightly different from what I posted you can correct it.

---

### Post by Zom-b on 2009-05-24
> **drs305 said:**
> That is probably the line you added. You can open gedit and go directly to the bad line with this command:
```

gksudo gedit +14 /etc/fstab

```

You can post it or if it is slightly different from what I posted you can correct it.

ahh apparently I added some extra text that wasn't needed

---

