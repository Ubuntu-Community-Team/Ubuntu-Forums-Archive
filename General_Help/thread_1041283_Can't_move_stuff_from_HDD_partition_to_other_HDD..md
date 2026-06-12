---
title: "Can't move stuff from HDD partition to other HDD."
date: 2009-01-16
forum: General Help
---

### Post by Murdok09 on 2009-01-16
Hey everyone, I'm in trouble.

I had Ubuntu installed, on a portable WD harddrive. I then installed Vista on my internal HDD, and it screwed my PC. So I formatted my internal HDD and when I try to install ubuntu it says "ext3____ error". When I try to boot Ubuntu from my external drive, it says ubuntu isn't there. 

Now, I have two partitions - one 158 Ext3 and one 159 FAT32. I want to put everything from the 3 over to the fat32. When I look at the files, it has a box with an x on it and won't move. If I open sudo nautilus, and try, I can move SOME but not all; it says "invalid permissions". I have even tried moving to desktop THEN to other partition, but nothing. I don't know what to do, but if I don't get these files (which I CAN view and use, just not move) I'm going to kill a Canadian midget and then jump off Niagra falls.

Please help!
Thanks!

---

### Post by redilyn on 2009-01-16
Have you checked the fs for errors?

```

fsck.ext3 -f /dev/sdaX

```

Where X is your partition number.

---

### Post by wolfen69 on 2009-01-16
are you using a live cd to copy and paste these files?

---

### Post by Murdok09 on 2009-01-16
I'm booting from a flash drive ATM, but I want to move everything and install one the partition.

---

### Post by Murdok09 on 2009-01-16
> **redilyn said:**
> Have you checked the fs for errors?

```

fsck.ext3 -f /dev/sdaX

```

Where X is your partition number.

ubuntu@ubuntu:~$ fsck.ext3 -f /dev/sdc1
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Permission denied while trying to open /dev/sdc1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$

---

### Post by redilyn on 2009-01-16
```

sudo fsck.ext3 -f /dev/sdaX

```

---

### Post by Murdok09 on 2009-01-16
> **redilyn said:**
> ```

sudo fsck.ext3 -f /dev/sdaX

```

ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu@ubuntu:~$

---

### Post by redilyn on 2009-01-16
I notice the first time you tryed this you used sdc1 the second time was sda1

Are you sure you tryed the right partition the second time?

---

### Post by Murdok09 on 2009-01-16
Lol, nice catch. I didn't notice the code was different, I thought he just wanted me to use SDA, lol.

ubuntu@ubuntu:~$ sudo fsck.ext3 -f /dev/sdc1
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Superblock invalid, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$

---

### Post by Murdok09 on 2009-01-16
I went into sudo nautilus, and clicked the drive. Now I can LOOK at things. I tried to move a folder to the FAT32 partition, and this showed:

The folder "Videos" cannot be handled because you do not have permissions to read it.

---

### Post by redilyn on 2009-01-16
If you right click on that folder and choose properties then go to the permissions tab.

What does it show for owner and what are the permissions for group and other?

---

### Post by Murdok09 on 2009-01-16
Okay, for the ENTIRE folder, it is 1000 Create Delete, 1000 Access, and Others Access.

For specific folder, it is 1000 Create Delete, 1000 Access, and Others Access.

---

### Post by redilyn on 2009-01-16
Okay, I'm going to assume these folders are in your home folder. If not make the appropriate changes to the commands below

```

sudo chown $yourusername -R /home/$yourusername/
sudo chmod 755 -R /home/$yourusername/

```

---

### Post by Murdok09 on 2009-01-16
They WERE in my home folder. Now I am booting from essenially a Live CD. What do I use for a username? I cannot install Ubuntu until I move these files.

Thanks!

---

### Post by redilyn on 2009-01-16
Humm... good point

Okay, You will need to fill in the blanks here. You will need to chmod 777 the folder which contains the files you want to move. Since you are booting from a live cd I don't know exactly what folder they will be in. probably something like /media/disk/home/****/ where **** is the username you had setup on ubuntu before this happened.

So

```

sudo chmod 777 -R /media/disk/home/*****/

```

---

### Post by Murdok09 on 2009-01-16
Okay, the partition is named disk, and my username USED TO BE andrew. I am going to try what you did, and I'll post ASAP.

---

