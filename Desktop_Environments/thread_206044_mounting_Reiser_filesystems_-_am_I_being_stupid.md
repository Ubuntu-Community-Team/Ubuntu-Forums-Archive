---
title: "mounting Reiser filesystems - am I being stupid?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by truant on 2006-06-29
Hi,

I've just formatted my FAT32 partition as Reiser (to use as a backup drive for me and other network users in my house), and I can't for the life of me mount it read/write for all users.  I can mount it easily enough, but no matter what options I put into fstab, it always shows as being drwxr-xr-x when I clearly want drwxrwxrwx.  Chmod/chowning the mount point after mounting has no effect.

the relevant part of fstab currently reads:

```
/dev/hda5       /media/Spyglass reiserfs        defaults        0       1
```

But I've tried most combinations of user,rw,suid,dev,exec,etc in the options field as well.

The GUI disk management tool is no help, as it provides no options for permissions during mounting, and it doesn't appear to write anything to fstab anyway.

Am I just being dense, or have I missed something?  Any help would be appreciated.

---

### Post by tonyr on 2006-06-29
Have you tried option **umask=0**?

---

### Post by truant on 2006-06-29
Yup, tried that.  Sorry, forgot to mention it.  umask is not a valid option for Reiser filesystems, the mount fails..

---

### Post by truant on 2006-06-30
Rebooted, was fine.   Not sure what happened.  Don't like it when reboots fix things.

Suspect confusing interplay of mtab, fstab and /proc/mounts was culprit.  Not sure why mtab would take priority over fstab in a mount -a situation, but there you go.  I never claimed to be a filesystem expert.  :)

---

