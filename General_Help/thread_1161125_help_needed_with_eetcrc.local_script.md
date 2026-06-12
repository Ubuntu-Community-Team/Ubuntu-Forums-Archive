---
title: "help needed with /eetc/rc.local script"
date: 2009-05-16
forum: General Help
---

### Post by chrisod on 2009-05-16
I'm fighting the known Jaunty bug that doesn't mount external drives at boot. I thought simply adding a *mount -all* to */etc/rc.local* would force the machine to mount all as about the last thing it does during boot. It's not working. I also tried just mounting a single file system that way with *mount /mnt/music* - that did not work either.

I also tried the commands with sudo - that didn't work either.

I'm starting to get into the habit of opening a terminal and typing *sudo mount -all* at every boot - but I'd really rather not have to do that. 

Does anybody know what I'm doing wrong with the /etc/rc.local script?

It's a network attached drive mounting with NFS - so the workarounds for USB drives do me no good.

---

### Post by dcstar on 2009-05-16
> **chrisod said:**
> I'm fighting the known Jaunty bug that doesn't mount external drives at boot. I thought simply adding a *mount -all* to */etc/rc.local* would force the machine to mount all as about the last thing it does during boot. It's not working. I also tried just mounting a single file system that way with *mount /mnt/music* - that did not work either.
........
It's a network attached drive mounting with NFS - so the workarounds for USB drives do me no good.

If it is related to the networking not actually starting until later in the boot process (which seems to be a 9.04 "feature") then it is pointless putting it in the rc.local **unless** you delay it with a command like this preceding it:

```
sleep 20
```

---

