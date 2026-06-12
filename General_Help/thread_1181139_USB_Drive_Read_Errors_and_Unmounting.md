---
title: "USB Drive: Read Errors and Unmounting"
date: 2009-06-07
forum: General Help
---

### Post by PirateChef on 2009-06-07
My USB external drive has started behaving very oddly. If I try to copy or otherwise access a certain directory, it'll give me a read error, and then unmount. It doesn't behave this way with the whole directory, though, just certain files in that directory. Some files behave this way consistently, others inconsistently.

I was afraid that the drive had overheated, because I leave it plugged in all the time. I started copying stuff off, in case it's getting ready to die. However, other parts of the drive seem to be working just fine.

What should I do?

---

### Post by SeanTater on 2009-06-07
This is rather general but there could be several reasons for it. If you have read/written/deleted about 50k to 100k files, you might have worn out the disk. Otherwise, I would do a file system check. Usually this can be done by first unmounting (but not unplugging) and the running:

```
sudo fsck.vfat /dev/DEVICE
```

If you don't know the name of the device - you might be able to find it in the properties of it (I'm not sure), or you can give a wild stab by looking at the capacities.

You can get the names and capacities this way:
```
df -h
```

---

### Post by PirateChef on 2009-06-07
It's not VFAT, it's ext2. I ran fsck when this problem first came up, and it gave me some message about altering the filesystem. I thought that'd fixed it, but it hasn't. I'm willing to run it again with different settings, but I want to get all of my files backed up, first.

---

### Post by SeanTater on 2009-06-07
Sorry, I don't have much beyond that. That's always fixed it for me.  "-p" helps if you're looking for options though.

---

### Post by PirateChef on 2009-06-08
I used 
```
e2fsck -p /dev/sdc1
```

and got this message:
```
/dev/sdc1 was not cleanly unmounted, check forced.
/dev/sdc1: Inode 3006465 ref count is 20, should be 19.  FIXED.
/dev/sdc1: 66252/6111232 files (3.4% non-contiguous), 14026779/24420800 blocks
```

The problem's still there, though.

---

### Post by PirateChef on 2009-06-15
OK, I was able to copy most of the files off, and then reformatted it to VFAT with mkdosfs. It's still having read problems, though. How can I run a test on the read/write functions?

---

