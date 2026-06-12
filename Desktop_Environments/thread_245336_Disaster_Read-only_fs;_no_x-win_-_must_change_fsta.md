---
title: "Disaster: Read-only fs; no x-win - must change fstab"
date: 2006-08-27
forum: Desktop Environments
---

### Post by jackn on 2006-08-27
Disaster has struck...

1. System loads as read-only.
2. No X-windows (totally unrelated to the recent update issue).
3. I am using live CD to consult.

This is probably due to a change introduced in /etc/fstab in the course of a beagle install,. I added 'CONFIG_EXT3_FS_XATTR' which seems to be the name of the kernel option for extended attributes. I should have added 'user_xattr', which is the proper extended attributes property.

In any case, the / directory (namely everything, though the /home directory is mounted separately), mounts as read-only. This must be due to a mount property which goes:
```
/dev/hda2       /      ext3    defaults,errors=remount-ro 0  1
```
(I did not include the above 'CONFIG_EXT3_FS_XATTR' mistake, but it's there). It is, I think, a default option, as I don't recall ever having put it in there myself.
Now, to recover the system from this SNAFU, I need to restore the /etc/fstab file, but... it's 'read-only'.

I have tried to modify it from the console logged in as my user, and from the console in recovery mode. Nothing doing - the file-system is mounted as read-only, and I can't write to the fstab file to restore it.

Can you help me get out of this mess?

Jackn

---

### Post by mssever on 2006-08-27
Try ```
mount -o remount,rw /dev/hda2
``` The default mount options for the root partition in fstab is to remount the partition read-only when there are errors, to prevent hosing your system.

You could also mount the partition from the live CD and fix it that way.

---

### Post by jackn on 2006-08-27
> **mssever said:**
> Try ```
mount -o remount,rw /dev/hda2
``` The default mount options for the root partition in fstab is to remount the partition read-only when there are errors, to prevent hosing your system.

You could also mount the partition from the live CD and fix it that way.

Thanks a bunch msserver, two great suggestions, how kind.

Fixed it off of the live CD. 

Again, proof of the incredible resilience of Linux and Ubuntu Linux. The users get a lot of power, which inevitably leads to some SNAFUs. But help and recovery are a few clicks away, as the power to set things right is as great. To think that, while I was surprisingly collected under the circumstances, I even contemplated the MS-Windows reinstall scorched earth tactics...

Thanks again.

Jackn

---

