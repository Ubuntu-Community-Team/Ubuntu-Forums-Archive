---
title: "Force disk check by time not mounts?"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Atomic Dog on 2006-10-03
I'm looking how to force a disk check every two months instead of 30 mounts.  Any idea how to set it??  I'm usually good at searching but I haven't come up with anything solid.  So I figured I'd actually ask a question for once :)

---

### Post by mitch.c on 2006-10-03
> **Atomic Dog said:**
> I'm looking how to force a disk check every two months instead of 30 mounts.  Any idea how to set it??  I'm usually good at searching but I haven't come up with anything solid.  So I figured I'd actually ask a question for once :)
Assuming they are ext2/3 filesystems:
```
# replace device with proper devicename
sudo tune2fs -c 0 -i 2m /dev/device
```

---

### Post by Atomic Dog on 2006-10-03
Thanks Mitch!  I appreciate it.

---

