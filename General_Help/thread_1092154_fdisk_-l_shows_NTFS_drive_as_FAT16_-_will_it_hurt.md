---
title: "fdisk -l shows NTFS drive as FAT16 - will it hurt?"
date: 2009-03-10
forum: General Help
---

### Post by mckechan on 2009-03-10
I just installed a 1TB internal HD. I formatted it in Windows to NTFS as one great big partition. I use it with Picasa in Windows, which is why I chose that format.

For every day use I use Ubuntu. When I run fdsik -l the new drive shows up as FAT16. However, I am mounting it as NTFS and it seems to work fine, although it still shows up as FAT16 under fdisk.

Is this going to come back and bite me?

Thanks,

Dave

---

### Post by unutbu on 2009-03-10
Partitions have a type and filesystems have a type. It sounds like you have a partition of type FAT16 and a filesystem of type NTFS inside it. I don't think this matters as far as Linux is concerned, though Windows might handle the partition differently based on partition type. (There are hidden partition types, for example, which Windows will hide...) So if you connect your drive to a Windows machine, the partition may or may not be readable. I'm not sure; you might want to try.

The following command changes the type of sdb1 to 7. The number 7 means an NTFS partition type.
```

sudo sfdisk -c /dev/sdb 1 7
```

To use this command, you might have to change "sdb" to something else, like "sda", "sdc" or "sdd", depending on how many drives you have, and the order in which they are listed. 

So first confirm the correct device name for your partition, and then you can try the command above, changing "sdb" to the appropriate letters.

---

### Post by mckechan on 2009-03-10
Thanks for replying so quick. It doesn't like the -c option

```
 sudo fdisk -c /dev/sdd 1 7
fdisk: invalid option -- c

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
```

looks like I want -b or -u. I'm not exactly sure what to try...

Thanks

---

### Post by unutbu on 2009-03-10
You scared me for a moment. The command is sfdisk, not fdisk. :)

---

### Post by mckechan on 2009-03-10
Ah! I always miss stuff like that, dangerous I know. Well, it had done the trick so thanks very much.

---

### Post by mckechan on 2009-03-12
Thanks again for your fix. Unfortunately I wanted to use the drive as an NFS share and I have now found out this is not so simple for NTFS in Ubuntu. I have seen some threads on the issue but have only found instructions in Spanish!

Is there a simple way around this?

---

### Post by unutbu on 2009-03-12
Perhaps try this:
[http://ubuntuforums.org/showthread.php?t=876943](http://ubuntuforums.org/showthread.php?t=876943)

Also, are you sure you want to use NFS? There are other ways to mount remote filesystems, such as [Samba]("https://wiki.ubuntu.com/ComprehensiveSambaGuide")  and [sshfs]("http://fuse.sourceforge.net/sshfs.html").

---

### Post by mckechan on 2009-03-12
I am using automount on my NFS shares with my macBook as a client. I use it as an alternative iTunes library, I find NFS is generally better/faster than using a firefly server.

I used to use samba, but I found it slow and I'm not sure how to set up automount. Since I am always switching networks between home/uni it is nice to just come home and have the share automatically available. 

Thanks for the link, I will try that, if not it won't be too much hassle for me to reformat as FAT 32...

Thanks

---

