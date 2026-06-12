---
title: "Read-only Automount"
date: 2009-01-29
forum: General Help
---

### Post by SidewinderX on 2009-01-29
When I plug in my external (WD Passport) hard drive (fs=fat32), Ubuntu is kind enough to automount it, however it is mounted in read-only mode (ro). My Segate external hard drive (fs=ntfs) automounts fine in read-write mode (rw). I suspect my WD Passport is mounted as ro due to its file system (however I really don't care why). That said, it becomes tedious unmounting the drive, then manually mounting the drive ```
sudo mount -t vfat /dev/sdb1 passport/
```

How can I tell Ubuntu (Intrepid) to automount this drive in rw mode?

Thanks,
John

---

### Post by Yashiro on 2009-01-29
in fstab:

> /dev/sdb1 /media/fat32   vfat  defaults,noauto,rw,user,umask=000   0   0 

That said I have the same setup as you and both ntfs and fat32 require no editting of any files for full access. I just plug in my usb drive and they're mounted with no issues.

---

### Post by SidewinderX on 2009-01-29
Right. That is how to mount the drive manually. My problem is, when it automounts (when I plug in the USB cable) it automatically mounts in read-only mode. Having to unmount it, then remount it manually (as you described) completely circumvents the reason of having it automount in the first place. I want it to automatically mount in read-write mode.

---

### Post by Yashiro on 2009-01-29
Well if you use the uuid instead in the fstab it should at least allow you to click the drive to mount it.
Is the drive read only to sudo, too?

---

### Post by SidewinderX on 2009-01-29
> **Yashiro said:**
> Is the drive read only to sudo, too?

Yes.

---

### Post by brallan on 2010-06-19
there are probably filesystem errors. Just open up the disk utility and run a filesystem check. then it should automount no problem.

System>administration>disk utility

unmount volume
filesystem check.

remount

worked for me!

---

