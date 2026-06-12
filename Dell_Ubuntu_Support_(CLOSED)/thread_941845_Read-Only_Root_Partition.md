---
title: "Read-Only Root Partition"
date: 2008-10-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LoganK on 2008-10-08
For some reason recently whenever I boot, X (and GDM) can't start because my root partition is mounted as read-only. I've edited and removed all references to read-only, readonly, ro, etc. from menu.lst and fstab but it still mounts as read-only when the system boots. At that point, I can login myself to a tty, drop to a root prompt, `mount -n -o remount rw /`, and resume normal boot and everything works fine--I can login to my normal user account, access the Internet, etc.. So the system is ok--just something, somewhere is setting / to mount as read-only on boot, and it's really annoying! Anyone have any ideas?

On an unrelated note, I like the cobwebs in the logo. :)

---

