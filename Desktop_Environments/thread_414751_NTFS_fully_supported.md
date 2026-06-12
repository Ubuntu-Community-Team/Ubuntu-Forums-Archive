---
title: "NTFS fully supported?"
date: 2007-04-20
forum: Desktop Environments
---

### Post by orange2k on 2007-04-20
Ive just installed feisty, and Ive noticed that I can access my XP NTFS disk partition without problem, so my question is if it is ok to write to this partition now?

---

### Post by mrazster on 2007-04-20
Even though writing to NTFS works..it's still concidered beta...and not recommende unless absolutely necessary.

---

### Post by rich.bradshaw on 2007-04-20
do add/remove programs, enable all available software in top right of window.

search for ntfs-3g and install. It will prompt you when installed to run it - enable write on all drives and it will be done. THis is version 1.0 of ntfs-3g now, so I think it is considered relatively bug free. I don't think you can write to the drives otherwise if you don't do this.

I use it everyday and have had no problems.

---

### Post by stefangr1 on 2007-04-20
NTFS-3G appears to have a stable release now. There are a lot of (very) positive statements on the ntfs-3g site, but i'm not sure how objective that is. I corrupted my ntfs-partition a few months ago, when I was using KTorrent to download a large file to it. Applications like this probably require a lot of small read/write activity. I recently spoke a (redhat) linux developer (who already warned me before, but I'm a bit stubborn), and he told me that ntfs is quite complicated to backward engineer, and that it's very difficult to get all bugs out of it therefore.

What do you guys think, does stable really means stable in case of ntfs-3g?

---

### Post by Pobega on 2007-04-20
Just install ntfs-3g and mount the Windows partition to any local folder, and r/w should work perfectly out of the box.

---

