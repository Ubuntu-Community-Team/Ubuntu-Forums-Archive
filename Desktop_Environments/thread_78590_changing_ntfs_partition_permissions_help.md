---
title: "changing ntfs partition permissions help"
date: 2005-10-18
forum: Desktop Environments
---

### Post by tellyousomeday on 2005-10-18
how do you change the permissions for ntfs partitions?

---

### Post by dbott67 on 2005-10-18
From within Ubuntu/linux?  This is a very dangerous thing to do.  By default, Ubuntu gives you READ ONLY permission.  Writing any changes to an NTFS partition from within Linux can cause data loss. 

If you want to be able to add/modify/delete data files from your NTFS partition, there are some newer utils that allow writing to NTFS (such as [Captive]("http://www.jankratochvil.net/project/captive/")), but you best backup your data before beginning.

The other alternative is to create a FAT32 partition to store data if you want to be able to work with your data files from either OS.

-Dave

---

### Post by jonesy on 2005-10-18
If you just want to change it so that when it's mounted your user has the read-only permissions instead of root then use the following command:

mount -t ntfs -o uid=username,gid=username /dev/device /mnt/mountpoint

You'll have to replace username, device, and mountpoint with the corresponding values for your setup, but that should mount the device so that your user has read / access permissions to the entire directory structure.

---

### Post by seldenthuis on 2005-10-18
Or you can use 'mount -t ntfs -o umask=02222 /dev/device /mnt/mountpoint'.
This gives every user read-only permissions.

---

### Post by gherson on 2005-10-19
Add remount: 'mount -t ntfs -o umask=02222,remount /dev/device /mnt/mountpoint' to easily test new mount options.

One thing that threw me off is that in Live 5.10, your umask, uid, and gid mount options will only be respected below /mnt/mountpoint, not in /mnt/mountpoint itself (where everything was always --xr--r--  root root).

george

---

### Post by toujours on 2005-10-19
Is this stuff no longer documented someplace?

I've been trying to find the old html ubuntuguide which I used with Warty but all I can find is that awful Wiki - which in my opinion is far too destructured and disorganised to be of any real use...

EDIT : I found it !

[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

