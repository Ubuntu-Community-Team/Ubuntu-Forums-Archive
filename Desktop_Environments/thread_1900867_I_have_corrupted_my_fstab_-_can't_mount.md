---
title: "I have corrupted my fstab - can't mount /"
date: 2011-12-27
forum: Desktop Environments
---

### Post by pabc on 2011-12-27
This should be simple to fix but I'm failing.

I have some spurious characters in the first line of my /etc/fstab so cant mount /

I select M for manual recovery and plan to delete the dodgy letters but the system says it's readonly

What commands do I need to get write access to the file?

I can't seem to get it to mount in DSL live cd either - the /mnt/hdb5 exists but is empty

edit:
I cant mount it in DSL as it's ext4 and that doesnt appear to be supported
I cant unmount/ mount as writeable it in recovery mode as it's /

I'm trying 10.04 live cd next......

---

### Post by pabc on 2011-12-27
```
mount -o remount,rw /
``` gave me a writeable system. spurious letters from fstab removed. reboot and happy.

---

### Post by Bobhuber on 2011-12-27
Boot with the live CD and make your changes from there.

---

