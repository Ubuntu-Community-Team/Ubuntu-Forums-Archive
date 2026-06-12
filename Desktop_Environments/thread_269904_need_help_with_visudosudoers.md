---
title: "need help with visudo/sudoers"
date: 2006-10-02
forum: Desktop Environments
---

### Post by moore.bryan on 2006-10-02
*for whatever reason, the new 2.6.18 kernel won't automount my external hd, so i have to do it manually.  i wrote a script to do just that and added ```
username     ALL=(ALL) NOPASSWD:/bin/mount,/sbin/reboot,/sbin/shutdown
``` via visudo, but the mount command still tells me only root can perform the operation.  any ideas?*

---

### Post by mitch.c on 2006-10-02
> **moore.bryan said:**
> *for whatever reason, the new 2.6.18 kernel won't automount my external hd, so i have to do it manually.  i wrote a script to do just that and added ```
username     ALL=(ALL) NOPASSWD:/bin/mount,/sbin/reboot,/sbin/shutdown
``` via visudo, but the mount command still tells me only root can perform the operation.  any ideas?*

Works for me. When you call mount in your script are you forgetting to call sudo? Should be something like this:
```
!#/bin/bash
sudo /usr/mount -t fstype /dev/path /mnt/path
```
If you forget sudo, it won't work. I've made the mistake before.

---

### Post by moore.bryan on 2006-10-02
*i'll double-check and let you know... i probably forgot that.*

---

### Post by moore.bryan on 2006-10-02
*now gnome-volume-manager is automounting... what the ****?*

---

### Post by mitch.c on 2006-10-02
> **moore.bryan said:**
> *now gnome-volume-manager is automounting... what the ****?*
I'm not sure what you mean, could you clarify? Also, maybe post the contents of /etc/fstab, and we'll figure this out.

---

