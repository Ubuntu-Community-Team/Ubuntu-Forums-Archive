---
title: "Ideal File Structure, Cluster Size for Ubuntu Install to USB Powered HD?"
date: 2009-02-10
forum: General Help
---

### Post by Rubicon421 on 2009-02-10
I have an external, USB POWERED (no other power cord or supply) 320 Toshiba HD that I want to install Ubuntu 8.10 on. What is the ideal file structure and cluster size?

The options give in Vista for this drive are:

Cluster size - 512 b up to 64 kb with 4096 b as the default
NFTS or exFAT

Also, if I partition it and put Ubuntu on one partition then use the other partition for file storage to access in Vista and Linux, does it matter what file structure the file storage partition is?

---

### Post by ibuclaw on 2009-02-10
I wouldn't have thought that the cluster size would make any difference on Ubuntu.

As for filesystem structure:
```

Primary Partition 1    /        ext2    10-15GBs to allow growth/installation.
Primary Partition 2    /home    ext3    10-100GB depending on how large your personal files are.
Primary Partition 3             swap    approx. 1.5xthe amount of RAM

```

If you want any other partitions on the drive, you'll require an **Extended Partition** to host as many Logical partitions as you like inside.

Regards
Iain

---

### Post by Rubicon421 on 2009-02-10
Is the swap partition required or does it just help performance to have it on a separate partition? Should I use Vista's partition tool in the computer management program? And why did you list the first one as ext2? Where/what is ext1?

---

