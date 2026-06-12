---
title: "I need to force a drive to mount"
date: 2009-02-08
forum: General Help
---

### Post by RoyalStickman on 2009-02-08
I was running the new windows 7 beta when for reasons unknown to myself it crashed and will no longer boot and crashes every time I attempt to boot win7. I have an external hard drive that I would like transfer all my files to using ubuntu as the medium on my computer but since win7 didnt shut down properly I cant mount the drive. Is there anyway to force the drive to mount?


I'm pretty ignorant in these things so try and make any instructions simple.

---

### Post by taurus on 2009-02-08
Something like

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
```
Assuming /dev/sda1 is the ntfs partition you want to mount.

---

