---
title: "create ntfs partition from linux"
date: 2006-03-17
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-03-17
OK: I have a weird problem. When I try to make a partition using the windows installer, it just keeps telling me that the partition is not compatible with windows, that its not ntfs, and the win installer is also refuses to create an ntfs partition. Is there anyway I can do this from linux? I see that gparted can create partitions of various types, but the ntfs choice is greyd out, anyway to make it work?

---

### Post by slux on 2006-03-17
Seriously doubt it because Linux you can't even fully write to NTFS with the NTFS support in the kernel. You'd need a Windows-based livecd (BartsPE...) or something similar.

---

### Post by aysiu on 2006-03-17
You could try ```
sudo apt-get update
sudo apt-get install ntfsprogs
``` You could also trying to format FAT32 and then have Windows convert that to NTFS.

---

### Post by slux on 2006-03-17
Oh right, ntfsprogs contains a "mkntfs" utility. Sorry, was unaware of that. I had a similar problem a while ago though and it was partition table related.. The XP installer is pretty bad at figuring out unusual ones.

---

