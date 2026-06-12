---
title: "Partitions not listed in /etc/fstab - where are they configured?"
date: 2008-12-29
forum: General Help
---

### Post by bgiddins on 2008-12-29
When I compare /etc/fstab and /etc/mtab, there's a bunch more mounted file systems in mtab than there are configured in fstab - where is the configuration for these other mounts?

e.g. I was looking to remount /dev/shm with more space allocated to it for VMware tuning, but there's no mention of /dev/shm in /etc/fstab - but I can see it mounted in /etc/mtab - where's the original mount configuration kept?

If I add a new mount config for it in /etc/fstab, will that override or conflict with configuration elsewhere?

cheers

---

### Post by ianhaycox on 2008-12-29
Have a look in /etc/default/tmpfs

---

