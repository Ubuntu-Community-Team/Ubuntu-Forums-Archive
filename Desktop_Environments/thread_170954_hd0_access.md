---
title: "hd0 access"
date: 2006-05-05
forum: Desktop Environments
---

### Post by azray on 2006-05-05
In previous attempts to run linux (SuSE) I was able to access files on the windows c: drive hd0. With Ubuntu installed on my second drive (hd1) I cannot access files on the Windows ntfs drive. I would like to do that so I can use Wine to run Quicken for example. Must be a way eh?  Thanks for any help

---

### Post by matthewstory on 2006-05-05
you can read from the files, but you can't write anything, so running a program on a different partition wouldn't work.  Suse is the same way, you can read but you can't write.

---

### Post by louis_nichols on 2006-05-05
I think you should offer a better description on what you understand by "accessing"

From the way you name drives, it would suggest something about grub, because it's the one that counts drives with hd followed by a number, starting from 0

linux sees them as hda (primary ide master), hdb (primary ide slave), hdc (secondary ide master), hdd (sec ide slave)

as for fat and ntfs it is true what matthewstory says that with ntfs you'll only be able to read, not write (yet - actually it is possible, but not enough tested sufficiently to be considered safe enough). The question is, though, what exactly you did to try to access your drive and what happened.

Also, are you talking about physical drives, or partitions? Windows makes no difference between them: it will just give them a letter, in order, but for Linux it's quite different. You can have hda1, hda2 etc for the first drive and hdb1 hdb2 etc for, say, the second

---

### Post by azray on 2006-05-05
I wish to read only I assume since I want to run Quicken using Wine. I have ubuntu loaded on the slave drive (hdb). QW.exe is on HDA windows address C:\progran files\quicken\qw.exe.

---

### Post by louis_nichols on 2006-05-06
well then... [this page]("https://wiki.ubuntu.com/MountingWindowsPartitions?highlight=%28windows%29") should be what you need :)

Breezy and dapper also have instructions for this under System/Help. I dunno about Hoary...

---

