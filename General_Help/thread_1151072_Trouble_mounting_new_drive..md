---
title: "Trouble mounting new drive."
date: 2009-05-06
forum: General Help
---

### Post by shamusl on 2009-05-06
I followed the instructions here:

[http://ubuntuforums.org/showthread.php?p=7194774](http://ubuntuforums.org/showthread.php?p=7194774)

and after rebooting, my machine says that I no longer have permissions to mount this partition.

---

### Post by logos34 on 2009-05-06
which partition are you trying to mount, what type of filesystem, etc?  What exactly did you type?

sudo fdisk -l

cat /etc/fstab

---

### Post by shamusl on 2009-05-06
> **logos34 said:**
> which partition are you trying to mount, what type of filesystem, etc?  What exactly did you type?

sudo fdisk -l

cat /etc/fstab

```

UUID=72380a61-4046-4e6a-b919-7be9f6c12eb4 /media/storage ext4 defaults 0 2

```

From the fstab document.

---

### Post by taurus on 2009-05-06
Post the outputs of these commands too.

```
sudo fdisk -l
sudo blkid
ls -la /media
df -h
```

---

### Post by shamusl on 2009-05-06
> **taurus said:**
> Post the outputs of these commands too.

```
sudo fdisk -l
sudo blkid
ls -la /media
df -h
```

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60546054

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14023   112639716    7  HPFS/NTFS
/dev/sda2           14024       28085   112953015   83  Linux
/dev/sda3           28086       28340     2048287+  82  Linux swap / Solaris
/dev/sda4           28341       30401    16554982+  83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009a129

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux


```

```

/dev/sda1: UUID="0EF4E29AF4E28377" TYPE="ntfs" 
/dev/sda2: UUID="8462bd16-ff98-4988-954a-65e5b78da1cc" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="8ad7d88c-a4e0-4106-a279-0a8857b6cfcb" 
/dev/sda4: UUID="b22e12e6-6929-4997-9762-ccec7133c5ff" TYPE="ext3" 
/dev/sdb1: LABEL="Storage" UUID="72380a61-4046-4e6a-b919-7be9f6c12eb4" TYPE="ext4" 

```

```

total 24
drwxr-xr-x  6 root root 4096 2009-05-06 14:25 .
drwxr-xr-x 22 root root 4096 2009-05-06 16:31 ..
lrwxrwxrwx  1 root root    6 2002-01-01 00:23 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2002-01-01 00:23 cdrom0
lrwxrwxrwx  1 root  999    7 2002-01-01 00:23 floppy -> floppy0
drwxr-xr-x  2 root  999 4096 2002-01-01 00:23 floppy0
-rw-r--r--  1 root root    0 2009-05-06 14:25 .hal-mtab
drwxr-xr-x  2 root root 4096 2009-05-01 19:36 sdb1
drwxr-xr-x  2 root root 4096 2009-05-01 19:36 second

```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              16G  5.0G   10G  34% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  268K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  156K  1.6G   1% /dev
tmpfs                 1.6G  380K  1.6G   1% /dev/shm
lrm                   1.6G  2.4M  1.6G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda2             107G   95G  6.9G  94% /home

```

If there is any other information that you would like me to provide/ need me to provide just let me know.

"Storage" is the volume I am trying to mount.

---

### Post by taurus on 2009-05-06
You need to create that new mount point since there is no storage in /media right now.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```

---

### Post by shamusl on 2009-05-06
> **taurus said:**
> You need to create that new mount point since there is no storage in /media right now.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```

Will this now auto-mount on boot?

---

