---
title: "A few seconds after boot, ntfs drives disappear"
date: 2018-10-29
forum: Desktop Environments
---

### Post by vidtek on 2018-10-29
I have been struggling with this for a few days now, after a few days away in beautiful Torquay, this problen arose. 

After booting up and logging in there is a short window in time when the entries in my fstab are valid, then a few seconds later all my ntfs drives just vanish.

Here is my fstab: ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=6c0ab85c-3f8b-4b7c-8ef1-b0ed9ae4d8ad /               btrfs   defaults,subvol=@ 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=B60D-32FF	/boot/efi	vfat	defaults	0	1
# /home was on /dev/sda8 during installation
UUID=c68f50bd-e237-4b5b-b12e-ba909f3b1138 /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda7 during installation
UUID=59fa6452-d971-43d3-8dff-dcae4decb78f none            swap    sw              0       0
UUID=F2E89BB2E89B7397	/media/data	 ntfs-3g	defaults,rw	0	0
UUID=6E66CE4866CE112F	/media/tv	ntfs-3g		defaults,rw	0	0


```

I use nfs, this is my exports file: ```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#


/media/data 192.168.0.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/tv 192.168.0.0/24(rw,nohide,insecure,no_subtree_check,async)
```

This is the result I get from Dolphin when it fails: [ATTACH=CONFIG]281483[/ATTACH]


I am really stumped, why should it work for just a few seconds?  It doesn't make sense to me at all.:confused::confused::confused:

Tony

---

### Post by ajgreeny on 2018-10-30
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 

See [https://ubuntuforums.org/showthread.php?t=2404907](https://ubuntuforums.org/showthread.php?t=2404907) which is answered.

Closed.

---

