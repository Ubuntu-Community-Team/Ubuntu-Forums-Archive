---
title: "Convert EXT3 FS partition to ReiserFS"
date: 2005-12-08
forum: Desktop Environments
---

### Post by St3althcAt on 2005-12-08
Hello!
Well, the tilte of the post has almost all: is it possible to convert my EXT3 FS partition to ReiserFS withou formatting or loosing data? Windows, for example, can convert FAT32 to NTFS. Just an example. Thank you for the attention.

By the way, about 2-3 months running Linux, don't know exactly, and I'm loving it... Well, I get fed up with it some times, I must confess, mainly when I've problems with it, but soon or later I get back to Linux! :P Still not reached the light, I think, but I'm seeing it! :P

---

### Post by cwaldbieser on 2005-12-08
[QUOTE=St3althcAt]Hello!
Well, the tilte of the post has almost all: is it possible to convert my EXT3 FS partition to ReiserFS withou formatting or loosing data? Windows, for example, can convert FAT32 to NTFS. Just an example. Thank you for the attention.

By the way, about 2-3 months running Linux, don't know exactly, and I'm loving it... Well, I get fed up with it some times, I must confess, mainly when I've problems with it, but soon or later I get back to Linux! :P Still not reached the light, I think, but I'm seeing it! :P[/QUOTE]
I don't think you can upgrade the filesystem this way.  You would need to mount a new ReiserFS volume and migrate the data (maybe with "dd").  It is probably just easiest to wait until such a time as you are going to repartition or get an extra drive.

---

