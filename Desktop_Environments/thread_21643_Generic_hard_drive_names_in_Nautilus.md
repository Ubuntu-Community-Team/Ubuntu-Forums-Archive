---
title: "Generic hard drive names in Nautilus?"
date: 2005-03-23
forum: Desktop Environments
---

### Post by statico on 2005-03-23
I have partitions listed as user-mountable in /etc/fstab. When navigating to "Computer" with Nautilus, the names of the volumes are rather generic: "124G Hard Drive: 124G Media."

I can't rename these volumes from the Properties dialog. Any ideas how I could change these names?

---

### Post by Julius on 2005-03-23
Well that's because you have the 'user' thing in /fstab. They should appear with their mounting location name (windows if it's mounted on /media/windows), but for some reason they don't. :P 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641)

---

### Post by statico on 2005-03-23
It's more convenient for me to be able to user-mount the volumes, so I'll stick with the generic names. Thanks!

---

