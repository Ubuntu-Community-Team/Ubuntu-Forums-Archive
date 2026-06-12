---
title: "gparted question"
date: 2008-12-19
forum: General Help
---

### Post by LewisHardbone on 2008-12-19
Hello all,
I was doing a move to the right in GParted and didn't realize how long it was going to take - apparently it is copying empty space and taking forever doing it. I only have 20 GB on the 500 GB drive, so I'm wondering if it will be okay to cancel the move after it's copied the 20 GB? I figure that the data itself would be moved, and the rest is just empty anyway, but I'm wondering if maybe it starts at the other end or it would screw something up regardless.

Thanks

---

### Post by killersnowgoon on 2008-12-19
i would just wait. it might not do anything if you cancel it, but the risk of corrupting your hard drive outweights the hour you might save

---

### Post by dcstar on 2008-12-19
> **LewisHardbone said:**
> Hello all,
I was doing a move to the right in GParted and didn't realize how long it was going to take - apparently it is copying empty space and taking forever doing it. I only have 20 GB on the 500 GB drive, so I'm wondering if it will be okay to cancel the move after it's copied the 20 GB? I figure that the data itself would be moved, and the rest is just empty anyway, but I'm wondering if maybe it starts at the other end or it would screw something up regardless.

Thanks

You may be ok if you cancel before it moves your data, but the way filesystems like EXT2 spread file data through the available space may mean that you will risk losing stuff.

Better to let it run its course.

---

