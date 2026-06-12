---
title: "Using cpio to extract initrd.img"
date: 2005-11-15
forum: Desktop Environments
---

### Post by stuporglue on 2005-11-15
Hi, 

I have an odd machine, and need to edit my initrd.img to get some critical drivers to load nice and early in the boot process. 

I can't seem to find any good tutorials on how to do this. The best I've found is bits and pieces on line. 

So far, I've got it un-gzipped.
```
gunzip -dc initrd.img > initrd.unzipped
```
I can't get it to loopback mount, and it doesn't seem to be all the way uncompressed. Unfortunately, I don't know how to extract the fs from cpio. 
```
root@ubuntu:/tmp# file initrd.unzipped
initrd.unzipped: ASCII cpio archive (SVR4 with no CRC)

```

Any help would be greatly apreciated!

---

### Post by psusi on 2005-11-15
cpio is an archive format like tar, you don't mount it.  Rather than mess with cpio to extract, modify, and archive your initramfs, you would be better off customizing mkinitramfs to build new images with the drivers that you need.  

Look in /usr/share/initramfs-tools.  The scripts in the hooks directory are called by mkinitramfs, and from there you can use functions provided to copy in binaries or drivers.  The scripts directory is copied into the initramfs and these are run during bootup.  

If you really want to extract the cpio archive, after gunzipping it, IIRC, the command is cpio -i foo.cpio.

---

### Post by stuporglue on 2005-11-15
Isn't the initrd.img a disk image though? That was my impression, though it appears I was wrong. :-) 

I might still try extracting and repackageing the cpio. It's for a old Mac that won't boot propperly yet, and I don't have another computer with the Mac modules etc. I think I can fix my problem just by editing one of the startup scripts. 

Thank you!

---

### Post by psusi on 2005-11-16
The old form of initial ramdisk was a disk image, usually of a romfs filesystem.  These days it has been replaced by the initramfs system, which uses a cpio archive to contain the boot files.  The name initrd seems to have stuck though.

---

