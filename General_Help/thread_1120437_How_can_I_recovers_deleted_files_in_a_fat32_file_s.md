---
title: "How can I recovers deleted files in a fat32 file system ?"
date: 2009-04-09
forum: General Help
---

### Post by brijith on 2009-04-09
Hai all,

I would would like to know how to recover deleted files in a windows file system from Ubuntu. I was a windows xp user but now I use only hardy.
is there any graphical tool that will help me ....


**[COLOR="Sienna"]Thanks For Your Help[/COLOR]**

---

### Post by dcstar on 2009-04-09
> **brijith said:**
> Hai all,

I would would like to know how to recover deleted files in a windows file system from Ubuntu. I was a windows xp user but now I use only hardy.
is there any graphical tool that will help me ....


```
man ntfsprogs
man ntfsundelete
```

---

### Post by brijith on 2009-04-10
> **dcstar said:**
> ```
man ntfsprogs
man ntfsundelete
```

it seems to be for NTFS .. 
I need one for fat32

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by mb_webguy on 2009-04-10
Use [TestDisk]("apt://testdisk").  [Here's how]("http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_FAT").

---

