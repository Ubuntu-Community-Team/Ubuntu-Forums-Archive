---
title: "Trash Can on NTFS Partition?"
date: 2008-12-20
forum: General Help
---

### Post by joeyknuccione on 2008-12-20
I've got an NTFS partition I use for storing my personal files. Is there any way I can create a trash can on this partition?

In googling I found a thread that sad how to do it in FAT32, but it didn't work.

Please help.

---

### Post by TheMyself on 2008-12-23
I have the same problem. I can't move files on the NFTS partition to trash. I can just delete them "permanently". Can't files in the NTFS partition be moved to ext3's trash?  :confused:

---

### Post by logos34 on 2008-12-23
> **joeyknuccione said:**
> I've got an NTFS partition I use for storing my personal files. Is there any way I can create a trash can on this partition?



I thought it created a '.user-Trash' or whatever when you deleted sth...then you can in turn delete the '.user-Trash'

---

### Post by TheMyself on 2008-12-24
Yes. There is a hidden folder ".Trash-0" (and this must be the case for joeyknuccione as well)   but I can delete files into it only when I start nautilus (or other applications) as root. Is there any way that I can make the NTFS partition my own? (like home folder) It's physically  my own!

---

### Post by Laibcoms on 2009-01-14
to the OP: I assume that you delete the .Trash folder on your NTFS drives via Windows before and now it won't recreate the folder if you delete a file via Ubuntu?

If that's the case, I have the same issue.  In Ubuntu, the .Trash is hidden by default.  When you log-in back to Windows, they're not, and you'll see that you have plenty of deleted stuff eating your HD Space.

I am also looking for a way to tell Ubuntu to recreate the .Trash folder on NTFS drives... to no avail.

:/

Hope someone knows how.
For now, for my other drives (and USB drives), I just delete the contents of the .Trash folder instead of deleting the folder itself.  You have to press CTRL+H tho to show all hidden files in Nautilus.

---

