---
title: "defrag fat?"
date: 2008-12-17
forum: General Help
---

### Post by theevilhamster on 2008-12-17
I'm very aware that the ext3 FS suffers very little form fragmentation problems, so should not need a defrag, but I also mange some drives that are fat formatted on my system. What is the best way of defragging these under linux?

Thanks a lot :)

---

### Post by jerome1232 on 2008-12-17
As I understand it there currently are no tools to defrag fat or ntfs volumes from Linux, generally you'll have to use Windows to defrag those. I guess the reason it hasn't been developed is most people that use fat/ntfs are sharing the drive with a Windows computer and it can be defraged there.

---

### Post by theevilhamster on 2008-12-17
Thanks a lot, I guess i will have to use windows for it :|:mad:. i'll wait in case someone else knows of a utility though.

I mainly use my external drive under linux, just need to use in windows every now and then, so a util to defrag would be great. thats why i dont want to use ext3 or anything else on it, just to rule that out.

i hate windows :mad:.

---

### Post by |{urse on 2008-12-17
is this hammy from #alternative?

---

### Post by ibuclaw on 2008-12-17
There is a basic script written in python here:
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)
But it doesn't really "defrag" as such...
Just makes a copy of the file and compares the two fragments. If it is less fragmented, it is kept and written over the old file, if it is more fragmented, it is removed/skipped and the next file in line is copied... etc.

Other than that, I'd recommend that you use a Windows app to defrag your hard drive.

Regards
Iain

---

