---
title: "How to change .kde settings directory?"
date: 2009-07-03
forum: Desktop Environments
---

### Post by barna on 2009-07-03
Hi,
I have tried kubuntu 9.10, but had to fall back to the good old 7.10, because my graphics card does not work correctly now, and many kde4 applications have lost a lot from their functionality compared to kde3.
But sometimes I want to boot to 9.10. The problem is, that both kde3 (of ubuntu 7.10) and kde4 (from ubuntu 9.10) use the same config directory: ~/.kde. Where can I change it so that for example kde4 uses .kde4?
Thanks
D

---

### Post by ajgreeny on 2009-07-03
I suspect you will need to have separate /homes for each install, instead of the same one for both, which I assume you must be using at the moment.  You can, however, use a shared data folder or partition.  That way all the configs related to the different versions of kde will be kept apart, but your data files will be available to both.

---

### Post by barna on 2009-07-03
I don't see why I would need separate /homes. In fact, I want to avoid this. It would be sufficient if kde3 and kde4 would use different config folders, for example /home/username/.kde3 and /home/username/.kde4, as it is the case with other distros. IF it's not a compile-time setting, which is the config file which contains the names of these folders?
Thanks

---

### Post by ajgreeny on 2009-07-03
OK, you know more about kde than I do, obviously, as I assumed all the kde configs were in the same place in all distros - shows how much I know!  I hope you can sort this out some way.

---

