---
title: "file system for mac windows and ubuntu"
date: 2009-03-02
forum: General Help
---

### Post by onesojourner on 2009-03-02
I have been triple/quadruple booting my system for a while now. I play games so I have windows, I do all my photo and video editing on OSX and then I do everything else on my ubuntu/kubuntu installs. I would like to to be able to access all my files between the operating systems. I have been using xfs for a while now but I can only access that from my linux OS. So far the only option I can find is just to use ntfs for my storage drives. Are there any other options out there?

---

### Post by 67GTA on 2009-03-02
To have read and write access across all OS's, it would be NTFS or FAT32. FAT32 has a 4GB file limit when moving files, so I would suggest staying with NTFS.

---

### Post by avtolle on 2009-03-02
+1 for NFTS.

---

### Post by onesojourner on 2009-03-03
thats what I figured. I was hoping for some secrete way to get xfs working but this will have to do.

---

### Post by mb_webguy on 2009-03-03
If Linux is one of your primary OSes, you might want to consider using ext3.  Windows can access ext2/ext3 filesystems using [Ext2 IFS]("http://www.fs-driver.org/"), and Mac OS X can access ext2/ext3 filesystems using [ext2fsx]("http://sourceforge.net/projects/ext2fsx/").  Neither of these drivers can use ext3 journaling, and mount an ext3 filesystem as ext2.  But afaik only Windows can do ntfs journaling, so you're not really any worse off unless Windows is your primary OS.

---

