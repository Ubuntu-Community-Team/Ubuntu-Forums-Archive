---
title: "home filesystem became read-only"
date: 2009-06-23
forum: General Help
---

### Post by lipinski on 2009-06-23
Never had this happen before, but I noticed that today I started getting some strange errors in VirtualBox - complaining about delayed writes in my Guest OS (Win XP), when I tried to restart the VM, VirtualBox wouldn't even start because it couldn't modify the Virtualbox.xml.

So, I narrowed it down to my home filesystem is somehow read-only.  The strange thing is that mount doesn't indicate it is read-only, and it wasn't read-only as of yesterday (was powered up all night).

From mount (not ro):
/dev/sda11 on /home type ext3 (rw,nosuid,nodev,relatime)

When I try to create a file in my home dir:
touch ~/test
touch: cannot touch `/home/<username>/test': Read-only file system

Only thing I can find possibly related in /var/log/messages:
kernel: [175152.058285] sd 1:0:1:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

I'm guessing that I need to reboot to clear this up, but I wanted to investigate first to see if I have some underlying problem that I need to fix to avoid this again (or data loss).  So, any ideas on other things to look for to find what's going on here?

I've backed up my home filesystem to another drive.

Thanks for any and all help.

---

### Post by dcstar on 2009-06-24
> **lipinski said:**
> Never had this happen before, but I noticed that today I started getting some strange errors in VirtualBox - complaining about delayed writes in my Guest OS (Win XP), when I tried to restart the VM, VirtualBox wouldn't even start because it couldn't modify the Virtualbox.xml.

So, I narrowed it down to my home filesystem is somehow read-only.  The strange thing is that mount doesn't indicate it is read-only, and it wasn't read-only as of yesterday (was powered up all night).

From mount (not ro):
/dev/sda11 on /home type ext3 (rw,nosuid,nodev,relatime)

When I try to create a file in my home dir:
touch ~/test
touch: cannot touch `/home/<username>/test': Read-only file system

Only thing I can find possibly related in /var/log/messages:
kernel: [175152.058285] sd 1:0:1:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

I'm guessing that I need to reboot to clear this up, but I wanted to investigate first to see if I have some underlying problem that I need to fix to avoid this again (or data loss).  So, any ideas on other things to look for to find what's going on here?

I've backed up my home filesystem to another drive.

Thanks for any and all help.

If this is in your fstab file, then an error will cause a RO remount:

```
errors=remount-ro
```

---

