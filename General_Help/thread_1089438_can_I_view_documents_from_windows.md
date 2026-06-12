---
title: "can I view documents from windows"
date: 2009-03-07
forum: General Help
---

### Post by makhaucrazy on 2009-03-07
Which file system should I use for partitioning if I wanted to edit and view my files in xubuntu when logged on to windows xp

---

### Post by martrn on 2009-03-07
ext2 - see [http://www.fs-driver.org/index.html]("http://www.fs-driver.org/index.html").

I would not say any other.

---

### Post by x33a on 2009-03-07
you cannot view linux filesystem from windows natively. and linux cannot be installed on ntfs/fat32 etc. 

to view linux fs from within windows you can use ext2fs, provided the linux fs is either ext2 or ext3.

---

### Post by martrn on 2009-03-07
You can set up symbolic links from your xubuntu (your home partition) to your files on your windows system you can edit and store documents on your windows ntfs disk  from xubuntu.

eg.
ln -s /mnt/windisk/users/myname/mydocuments /home/myname/winfiles

and then you have read/write acsess to your windoze files from xubuntu.

Other than that use fs-driver in windows to copy your file across, then edit it, then copy it back again.

Not perfect but better than webi.

---

