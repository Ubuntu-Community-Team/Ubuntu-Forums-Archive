---
title: "File premissions keep changing"
date: 2008-07-23
forum: Desktop Environments
---

### Post by bradcarr on 2008-07-23
I have an usb external that I have have been able to write too for several months now and this morning I was trying to copy some files over and it keep saying " Read ony file system". I can unmount, then remount and I an able to write to it for a little while, but it starts say Read only again. When I go in and try to do a "sudo chmod 777" it gives me "chmod: changing permissions of `external/': Read-only file system." Please forgive if this is something due to stupidity!

THANKS IN ADVANCE

---

### Post by Gatemaze on 2008-07-23
have you tried firstly an ls -l on the drive? this will saw you who is the "owner" and the group of the files as well as their permissions.... then you can get some more clues... cause if it owner is you, group ok, permissions ok, then something seems wrong... maybe backup your files, run a fsck on the drive and maybe reformat it?

---

### Post by bradcarr on 2008-07-23
drwx------ 5 username root 32768 1969-12-31 18:00 LACIE

My bad, I should have posted this earlier.
I funny thing is it doesn't change. When I remount the drive everything looks OK, an hour later all the folders have the little locks above them. I am doing something wrong?

---

### Post by vanadium on 2008-07-23
As Gatemaze suggested already, run a fsck.

---

### Post by bradcarr on 2008-07-23
Will do. thanks V

---

### Post by bradcarr on 2008-07-23
Oh, I got another question. The file system is fat16, am I able to run check disk. If so what would the it look something like "username@ubuntu:/ fsck /media/lacie/. ?????

---

### Post by sammydee on 2008-07-23
Fat16 does not support file permissions. The only permissions that apply are the ones it is mounted with.

If it is chaning by itself a little while after mounting I've no idea what is going on though :-/

---

### Post by vanadium on 2008-07-23
For the example, I assume that the device name of your partition is /dev/sdc1. You need to unmount, then run the diskcheck.

```

sudo umount /dev/sdc1
sudo fsck /dev/sdc1

```

fsck should automatically detect this is a fat16 drive and run dosfsck. You can run it directly with "sudo dosfsck /dev/sdc1"

```

man dosfsck

```
provides the documentation.

---

### Post by bradcarr on 2008-07-23
OK, I know this is going to sound insane, but I have been using transmission to download. never had a problem before and it downloads to my external ( the one I and having problems with). The whole time I have been having problems with this, transmission has been running. I remounted a couple of hours ago and have had no problems. I started transmission back up, a few minutes later I went into my external and the locks where back above the folders. Is there a connection somehow between the too?

---

### Post by Gatemaze on 2008-07-23
Maybe.... a complete speculation might be that transmission unmounts and remounts your drive with different permissions.

regarding fsck in terminal type fsck press tab twice and you will see a list of available fsck :)

---

### Post by Gatemaze on 2008-07-23
oooo and i would also suggest formatting it as fat32

---

### Post by bradcarr on 2008-07-23
it came back with 

fsck           fsck.ext2      fsck.minix     fsck.nfs       fsck.vfat
fsck.cramfs    fsck.ext3      fsck.msdos     fsck.reiserfs

---

### Post by bradcarr on 2008-07-23
Will I be able to format as fat32 under ubuntu

---

### Post by Yannick Le Saint kyncani on 2008-07-23
> **bradcarr said:**
> I started transmission back up, a few minutes later I went into my external and the locks where back above the folders. Is there a connection somehow between the too?

I'd say that transmission is using a file that's stored on a non working disk sector, so when reading/writing to it is failing, the kernel makes the dying disk read-only.

I'd suggest you check the output of "dmesg" when the disk becomes read-only and look for input/output errors.

---

### Post by bradcarr on 2008-07-23
dmesg says:

 3858.494378] FAT: Filesystem panic (dev sdb1)
[ 3858.494388]     clusters badly computed (126 != 119)
[ 3858.494394]     File system has been set read-only
[ 3860.131967] FAT: Filesystem panic (dev sdb1)
[ 3860.131976]     clusters badly computed (127 != 120)
[ 3862.282623] FAT: Filesystem panic (dev sdb1)
[ 3862.282633]     clusters badly computed (128 != 121)
[ 3863.817538] FAT: Filesystem panic (dev sdb1)
[ 3863.817547]     clusters badly computed (129 != 122)
[ 3867.138003] FAT: Filesystem panic (dev sdb1)
[ 3867.138012]     clusters badly computed (130 != 123)
[ 3869.760144] FAT: Filesystem panic (dev sdb1)
[ 3869.760153]     clusters badly computed (131 != 124)
[ 3877.642833] FAT: Filesystem panic (dev sdb1)
[ 3877.642842]     clusters badly computed (132 != 125)
[ 3877.642929] FAT: Filesystem panic (dev sdb1)
[ 3877.642932]     clusters badly computed (133 != 126)
[ 3877.643017] FAT: Filesystem panic (dev sdb1)
[ 3877.643020]     clusters badly computed (134 != 127)
[ 3877.643098] FAT: Filesystem panic (dev sdb1)
[ 3877.643101]     clusters badly computed (135 != 128)
[ 3877.643178] FAT: Filesystem panic (dev sdb1)
[ 3877.643180]     clusters badly computed (136 != 129)
[ 3877.643257] FAT: Filesystem panic (dev sdb1)
[ 3877.643259]     clusters badly computed (137 != 130)
[ 3877.643343] FAT: Filesystem panic (dev sdb1)
[ 3877.643345]     clusters badly computed (138 != 131)
[ 3886.556442] FAT: Filesystem panic (dev sdb1)
[ 3886.556452]     clusters badly computed (139 != 132)

I take it this is bad, if so would it be best just to format. This drive isn't six months old.

---

### Post by bradcarr on 2008-07-23
sudo dosfsck /dev/sdb1

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
path/to/file
  File size is 4551124 bytes, cluster chain length is > 4554752 bytes.
  Truncating file to 4551124 bytes.
path/to/file2
  File size is 2893237 bytes, cluster chain length is > 2916352 bytes.
  Truncating file to 2893237 bytes.
Free cluster summary wrong (10509894 vs. really 10509976)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdb1: 25418 files, 4748298/15258274 clusters

any idea's on how to fix.

---

### Post by Yannick Le Saint kyncani on 2008-07-23
> **bradcarr said:**
> dmesg says:

 3858.494378] FAT: Filesystem panic (dev sdb1)
[ 3858.494388]     clusters badly computed (126 != 119)
[ 3858.494394]     File system has been set read-only
[snip]
I take it this is bad, if so would it be best just to format. This drive isn't six months old.

Oh yeah, it's bad all right.

You should copy whatever you want to keep and don't have backup for to another drive and then _check for bad blocks_ while formatting.

If the disk does have bad blocks, you should not use it any more, that's just asking for trouble, and get another one.

---

### Post by bradcarr on 2008-07-23
Do I do that all from command line, if so how would it read or can I do that from the gui.

Thanks

---

### Post by Yannick Le Saint kyncani on 2008-07-23
> **bradcarr said:**
> Do I do that all from command line, if so how would it read or can I do that from the gui.

You can do that from anything you like, but remember that you won't be able to recover everything : you will get errors, some files/directories won't be copied because of the previous errors.

Just skip the unrecoverable files and proceed with the rest. Nautilus may provide a "skip" option when errors happen, I don't know (I'm just more confortable with the command line).

---

### Post by vanadium on 2008-07-24
To me, I do not have the impression that it concerns bad blocks here. It just concerns a fat16 file system that is already badly damaged. Because of this, accessing it causes inconsistencies that in turn cause linux to mount the file system read only to prevent further damage.

It comes back to my first post: check *and* repair the disk. After that, some files might be truncated or otherwise damaged, but the file system will be healthy again and you will be able to continue using the disk.

It might be easiest to run dosfsck with the -a option (automatic repair):

```

sudo dosfsck -a /dev/sdb1

```

You can also use the -r option instead (interactively) in which case dosfsck will prompt you before each correction.

That said, it would be wise to change this fat16 system to at least fat32. If you are only using the drive with Ubuntu, your best bet is to format it to the native linux file system ext3.

---

### Post by Yannick Le Saint kyncani on 2008-07-24
> **vanadium said:**
> To me, I do not have the impression that it concerns bad blocks here. It just concerns a fat16 file system that is already badly damaged.

Yeah, I don't know what made the filesystem inconsistent, bad blocks, software issues or unclean shutdown. However, I've suggested that he made a backup because it's always good to have a backup, especially in this situation.

As for the bad blocks or simply inconsistent filesystem, creating a new filesystem while checking for bad blocks is simple and leads to clear appreciation of the situation : either the disk has bad blocks and is dead (as in should be relied upon), or the disk has proved to have no bad blocks and the new empty filesystem is consistent.

---

### Post by vanadium on 2008-07-24
I fully agree.

---

