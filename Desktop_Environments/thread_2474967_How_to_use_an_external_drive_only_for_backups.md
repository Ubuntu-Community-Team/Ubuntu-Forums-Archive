---
title: "How to use an external drive only for backups?"
date: 2022-05-12
forum: Desktop Environments
---

### Post by greensage13 on 2022-05-12
I got an old notebook external, 250GB. I thought it might be convenient to use it as maybe some sort of backup for my PC here. I've had it for many years...probably 6. It's been shelved for 4+.

Would this be a good use for it and how would I go about doing this? Thanks.

---

### Post by GhX6GZMB on 2022-05-12
USB? Install a backup program, eg, Back-in-Time and plug it in.

---

### Post by #&amp;thj^% on 2022-05-12
If indeed for a system back up on XFCE and using such a tool as suggested by ml9104, it should be a mount in your fstab config.
It won't auto=mount which will cause problems with any back up tool used.

---

### Post by GhX6GZMB on 2022-05-12
A USB drive would normally auto-mount and Back-in-Time has no problems with that (unless it's unplugged).
Let's see what the OP returns with.

---

### Post by #&amp;thj^% on 2022-05-12
yep for manual back-up no problem, >>>automated or scheduled back-ups will need the mount in fstab>>>at least in my case usage.
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=7B02-353A                            /boot/efi      vfat    defaults,noatime 0 2
UUID=1b6cb1b8-4a0e-41aa-b6e3-23e8abd75cf8 /              ext4    defaults,noatime 0 1
/swapfile                                 swap           swap    defaults   0 0
/dev/disk/by-uuid/be93f3dc-cd54-4321-9a9f-558c1317fc44 /mnt/be93f3dc-cd54-4321-9a9f-558c1317fc44 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```
My permissions vary from normal user view though.

---

### Post by Tadaen_Sylvermane on 2022-05-13
I prefer systemd automounts myself.

```
192.168.1.2:/backups /backups nfs defaults,noauto,x-systemd.automount,x-systemd.idle-timeout=30 0 0
```

---

### Post by greensage13 on 2022-05-13
Thanks for the replies. I was planning on just plugging her in and letting it be. :) Just to get some use out of it. So Back-In-Time is what I should use?

---

### Post by #&amp;thj^% on 2022-05-13
> **greensage13 said:**
>  So Back-In-Time is what I should use?
As one choice, also another easy to use app is [TimeShift]("https://teejeetech.com/timeshift/") or [Borgbackup]("https://borgbackup.readthedocs.io/en/stable/installation.html") or even just[ rsync.]("https://manpages.ubuntu.com/manpages/jammy/man1/rsync.1.html")

---

### Post by ajgreeny on 2022-05-13
If you do choose eventually to just plug it in and let it automount it is essential to label the partition on the external drive to make sure it always mounts to the same **/media/label** folder.

Without that, and depending on what else might be attached, the disk could easily move from /dev/sdb to dev/sdc etc etc, meaning the backup application can not find the correct disk.

---

### Post by GhX6GZMB on 2022-05-13
> **ajgreeny said:**
> If you do choose eventually to just plug it in and let it automount it is essential to label the partition on the external drive to make sure it always mounts to the same **/media/label** folder.

Without that, and depending on what else might be attached, the disk could easily move from /dev/sdb to dev/sdc etc etc, meaning the backup application can not find the correct disk.

Never had this problem in my life.

---

