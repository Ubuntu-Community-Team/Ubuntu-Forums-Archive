---
title: "how do i add free space to a ext2 partition?"
date: 2009-03-29
forum: General Help
---

### Post by brayden13 on 2009-03-29
i have a partition already in use for ubuntu. I needed a bit more space so i downloaded the Parted Magic live CD and burnt it to a cd. then i booted up in it and opened up gparted. deleted a partition i didn't need (stupid HP recovery partition) and then applied that. it was then unallocated space after that.

then when i tried to add that free space to my existing ubuntu partition that is ext2 file system it just acted as if there was no space to add and just didn't allow me to add any more. it didn't come up with any error at all.

I really need this problems solved, I would rather not reinstall ubuntu but if i have to i guess i'll just have to.

---

### Post by carnauth on 2009-03-29
The partitions have to be one contiguous section. do you have a partition between the one you are wanting to expand and the free space;Or possibly is it an extended partition.?  

sometimes you might have to make a series of operations to get the free space where u need it.

---

### Post by brayden13 on 2009-03-29
There is a windows partition, that might be causing some problems.

---

### Post by carnauth on 2009-03-29
is it possible that you do a move on the windows partition and slide it over to take up the free space then you should have the freespace on the side next to your linux partition then you should be able to expand the ext2 partition.

---

### Post by brayden13 on 2009-03-29
i'm not sure i'll be able to do that. it doesn't seem like i possibly could. well actually now that i think about it i might be able to but i would lose some data, i do not think it could move the data over.

---

