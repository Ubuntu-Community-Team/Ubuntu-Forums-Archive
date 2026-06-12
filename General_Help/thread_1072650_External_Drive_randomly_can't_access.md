---
title: "External Drive randomly can't access"
date: 2009-02-17
forum: General Help
---

### Post by madhatter563 on 2009-02-17
Im running ubuntu server 8.10 and have an external HDD (NTFS) connected.  The mount seems to work just fine, but sometimes it just says I cannot connect to the device.. Restarting then remounting the drive fixes it every time, but I dont want to have to reboot every time the drive has the issues.  Is there a command to perhaps ntfs-3g services or a service that deals with talking to that drive?  Thanks

---

### Post by InspiredIndividual on 2009-02-17
I might have had a similar problem. In my case it was caused by the fact I didn't unmount the drive properly before disconnecting it. Taking care of this solved the problem for me.

EDIT: By the way, I don't know a different solution from rebooting in case of an improper unmount, so I can't help you with that.

---

