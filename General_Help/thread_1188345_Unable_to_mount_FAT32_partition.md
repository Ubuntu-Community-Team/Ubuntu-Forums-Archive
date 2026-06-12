---
title: "Unable to mount FAT32 partition"
date: 2009-06-15
forum: General Help
---

### Post by kadath217 on 2009-06-15
I'm having some trouble mounting a FAT32 partition. Ubuntu saw it during installation of Jaunty and for the first couple of uses, but then I started getting a weird error when I clicked on the drive under "Places":

> cannot get volume.fstype.alternative FAT32

I tried to manually remount and edit fstab to get the drive to mount, but I just can't get it to work. Hopefully someone can tell me what I'm doing wrong.

First, I can see the partition using fdisk-l:
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080       13912    62918572+   b  W95 FAT32
/dev/sda3           13913       13977      522112+  82  Linux swap / Solaris
/dev/sda4           13978       19452    43977937+  83  Linux

```

I can also see the UUID using blkid:
```
/dev/sda1: UUID="1C6C30626C3038BA" LABEL="Windows" TYPE="ntfs" 
/dev/sda2: LABEL="STORAGE" UUID="5E50-284F" TYPE="vfat" 
/dev/sda3: TYPE="swap" UUID="41c65c63-959d-44e7-a63f-af27358f8036" 
/dev/sda4: UUID="14c0040f-bef1-4112-b409-ee1c35d69544" TYPE="ext3" 

```

Second, here's the line I added in fstab:
```
#STORAGE - Windows FAT32 Drive
/dev/sda2 /mnt/STORAGE vfat quiet,defaults,rw 0 0
```

(I've tried it with both the device location and UUID to no avail.)

Third, I tried the steps above again after creating a new mount point - just to see if that would work. The initial mount point was /media/storage; the second mount point was /mnt/STORAGE.

Even more strange, the partition does show up fine in Storage Device Manager, and I seem to be able to browse the files from there. But it will not show up under Places or in the File Browser, even after numerous attempts to "sudo mount -a".

Any ideas or suggestions?

---

### Post by StGeorge on 2009-06-15
Does it show up as a folder in Computer/File System/mnt/  ? 

CHMOD:
********************************

Enter the following commands into terminal:
***************************

sudo su

****************************

Your Password:
****************************

sudo chmod -R 777 /mnt/(Folder Name)

***************************

---

### Post by kadath217 on 2009-06-15
When I go to /mnt, there is a dir there for STORAGE. However, when I click on it, it's empty - it's clearly not mounting the drive there.

(I did try the CHMOD, too, but the permissions seemed to already be set.)

---

### Post by kadath217 on 2009-06-24
*bump*

Apologies for bumping so soon, but being unable to access the majority of my files makes Ubuntu all but unusable.

In the meantime, I tried re-creating fstab from scratch, but I'm still having the same problem.

---

### Post by egalvan on 2009-06-24
> **kadath217 said:**
> 
Third, I tried the steps above again after creating a new mount point - just to see if that would work.
 The initial mount point was /media/**storage**;
 the second mount point was /mnt/**STORAGE**.

Any ideas or suggestions?

Linux is case-sensitive...

so **storage** is *not* the same as **STORAGE**.

Also, unix-style naming conventions are to use lower case, and no spaces.
Linux adheres to this, so following it will make Linux life a little easier, especially the spaces...
 they are more difficult to work with on the cli...you need "escape" characters...

---

### Post by kadath217 on 2009-06-24
I really just put the second in all caps to help me distinguish from the first. I checked to make sure fstab matched the mount points in capitalization, and they did. So this isn't the problem...

---

### Post by merlinus on 2009-06-24
You might try this in fstab:

/dev/sda2 /mnt/STORAGE [SIZE=-1][FONT=Bitstream Vera Sans Mono]vfat defaults,utf8,umask=007,gid=46 0 1[/FONT][/SIZE]

---

### Post by kadath217 on 2009-06-24
> **merlinus said:**
> You might try this in fstab:

/dev/sda2 /mnt/STORAGE [SIZE=-1][FONT=Bitstream Vera Sans Mono]vfat defaults,utf8,umask=007,gid=46 0 1[/FONT][/SIZE]

That worked! I'm trying to follow what that last part changed, but I'm not quite making it all the way.

---

### Post by merlinus on 2009-06-24
Glad it worked.  Here are some details:

**defaults **the default** **options are: rw, suid, dev, exec, auto, nouser, and async.
**utf8** is 8 bit character encoding (compatible with ascii.) 
**umask** sets the default file permissions (ie. who can read, who can write, who can execute).  007 means that files you create will have group read/write/execute access. 
**gid** is the group id.
[FONT=Bitstream Vera Sans Mono]**0**[/FONT] tells fsck **not** to do a filesystem check on this filesystem during bootup.

---

### Post by kadath217 on 2009-06-24
Thanks. I understand the defaults, utf8, and umask, but I didn't know about the gid=46. That's great - I really appreciate it!

---

### Post by merlinus on 2009-06-24
Glad to be of assistance, and welcome to the ubuntu community!

---

