---
title: "Help cleaning windows virus?"
date: 2009-01-29
forum: General Help
---

### Post by LazyD on 2009-01-29
Hello,

First post here. I'm booting to an ubuntu cd in an attempt to access the partition that was in a windows laptop in order to remove some malware files. Can't find a way around it in windows due to the files always hiding themselves (using the hising hidden files and folders setting) despite having messed with the registry for ages.

I would just like to be able to see the contents of the laptops hard drive and delete files without messing up windows at all. When I try to open the drive in ubuntu I get an error saying it couldn't mount the drive. I'm sure I remember doing this before without having to run any commands and I could see all the data that was on the system while it was mounted in windows... ?

Any help and comments much appreciated.

---

### Post by 00Davo on 2009-01-29
What does the error message say?

If it mentions "unclean shutdown", or "$MFTMirr", you can run this:
```
ntfsfix /path/to/drive
```
(replace /path/to/drive with the /dev path listed in the error message)

After running the command, you should be able to mount fine.

---

### Post by LazyD on 2009-01-29
Went into it again with the hope of entering that command and it just mounted fine straight away, malwares gone.

Thanks anyway

---

