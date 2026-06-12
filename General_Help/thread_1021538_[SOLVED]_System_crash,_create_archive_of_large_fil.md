---
title: "[SOLVED] System crash, create archive of large file"
date: 2008-12-25
forum: General Help
---

### Post by cogitordi on 2008-12-25
I have two large files (3 GB, 4 GB) that are Virtual Box VDI files. I have in the past created zip archives of these. Now when I try to do so, my Ubuntu Heron AMD64 OS crashes. The computer shuts down. 

I am wondering if the latest updates have introduced a bug.

---

### Post by ajcham on 2008-12-25
This could be a hardware issue - try running a memtest to see if there are any problems.

---

### Post by cogitordi on 2008-12-26
The BIOS memory test passes. However, I can zip the same file on another Ubuntu system that is comparable in hardware. I will try swapping the RAM to see what happens.

---

### Post by cogitordi on 2008-12-29
It was a *heat* problem that would only manifest itself when I attempted to zip, bzip2, gzip, or 7zip a large file such as the one mentioned. The RAM DIMM nearest the CPU would grow too warm. I added a fan with a higher airflow and everything is better. No component damage, fortunately.

---

