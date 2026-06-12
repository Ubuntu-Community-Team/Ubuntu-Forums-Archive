---
title: "Is there a better way to share files between Ubuntu and Windows?"
date: 2009-06-15
forum: General Help
---

### Post by Aeph on 2009-06-15
I've been using dual-booting Ubuntu and Windows for a few years and I've always used an ntfs partition in Windows for my media (ie music, documents, pictures, video...) that I would mount in Ubuntu with fstab and access the files that way. This always has a few minor drawbacks, like needing root access to add files to the drive and both operating systems adding their own files and folders to the drive that clutter it up ($RECYCLE.BIN, config files...).

My question is this: is there a better way to create a sort of shared drive that can be easily accessed and written to by both Windows and Ubuntu that simply has the files and folders and as few other files as possible? Any ideas would be appreciated.

---

### Post by Cheesemill on 2009-06-15
You don't need root access to use a mounted NTFS partition, just change the ownership of the mount point to your user using chown:
```
chown -R username:usename /media/ntfs
```

Obviously substituting your username and mount point.

---

### Post by aysiu on 2009-06-15
Can you *chown* an NTFS partition? I don't think NTFS supports *nix permissions.

If you have NTFS-3G installed (which Ubuntu has by default in recent versions), it should mount read/write.

---

### Post by Cheesemill on 2009-06-15
I'd bet on you being correct aysiu.

I've never tried it myself with NTFS, but I use it for all my ext3 and NFS mounts so I just presumed it would work. Oh well, you can't be right all the time:)

---

### Post by aysiu on 2009-06-15
I think the /etc/fstab line should read something like ```
/dev/sda1 /media/ntfs ntfs-3g defaults 0 0
``` Can someone with a bit more NTFS experience (I use Ubuntu, my wife uses Mac OS X, so we have no NTFS drives any more) jump in and confirm, correct, or refute?

---

### Post by Aeph on 2009-06-15
> **aysiu said:**
> I think the /etc/fstab line should read something like ```
/dev/sda1 /media/ntfs ntfs-3g defaults 0 0
``` Can someone with a bit more NTFS experience (I use Ubuntu, my wife uses Mac OS X, so we have no NTFS drives any more) jump in and confirm, correct, or refute?

Yes, that's more or less what my fstab line looks like. I've never tried ntfs-3g though. I may do that.

---

### Post by aysiu on 2009-06-15
You should make sure it's installed, too. I think the package name is *ntfs-3g*, but you should double-check in System > Administration > Synaptic Package Manager

---

### Post by Aeph on 2009-06-15
Would it be better to use a different format, like FAT, for this?

---

### Post by JKyleOKC on 2009-06-15
> **aysiu said:**
> Can you *chown* an NTFS partition? I don't think NTFS supports *nix permissions.
While I've not tried writing to them yet, I'm accessing NTFS drives on this box without needing to chown them.

However it's worth noting that the chown recommendation refers to the mountpoint directory, NOT to the mounted partition. If you unmount the partition, there's no reason it should complain, and when the partition is remounted afterward, the new ownership should stick.

Finally, with the correct options in fstab there's no problem. Here's how my two NTFS drives are listed:
```

/dev/sdb1 /media/sdb1 fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
/dev/sdc1 /media/sdc1 fuseblk rw,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0

```
Checking the permissions, both have full read-write for all users!

---

### Post by ricardofilipemoreira on 2009-06-15
> **Aeph said:**
> Would it be better to use a different format, like FAT, for this?
you guys are complicating too much. using FAT32 doesn't require privileges to read/write and windows doesn't store so many files there. in windows xp you can turn off system restore (shadow copies in vista) and the recycle bin for specific partitions. ubuntu doesn't create folders you don't want. you may have to create a folder in that partition that you own so you can have write access to it through ubuntu.

---

