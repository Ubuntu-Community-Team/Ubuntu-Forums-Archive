---
title: "Mounting a drive through nautilus"
date: 2009-04-08
forum: General Help
---

### Post by Idefix82 on 2009-04-08
How does nautilus know how to mount a drive if there is no corresponding entry in fstab? I have no entry for my Windows partition in fstab, but if I click on it in Nautilus, it mounts the partition correctly. Where is the configuration stored?
Thanks!

---

### Post by mcduck on 2009-04-08
Nautilus doesn't actually do the mounting, and there is no configuration file (not in the sense that anything would be configured beforehands, but if you want to check things automounted drives appear in /etc/mtab).

Automounting of unconfigured drives is handled by HAL which simply detects the drive and it's file system on the fly and mounts it based on that information.

---

### Post by Idefix82 on 2009-04-08
Thanks a lot! That explains it!

---

