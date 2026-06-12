---
title: "Meh?????????"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by Reily on 2007-06-17
I need some help. I have been running Ubuntu 7.04 from my dvdr drive, and I want to know, If I were to install Ubuntu 7.04, would it overwrite my XP? Please help!

-Reily

---

### Post by wieman01 on 2007-06-17
No, it won't. It even lets you boot from either system afterwards. Ubuntu is taking good care of your Windows install, so don't worry. :-)

---

### Post by MetalMusicAddict on 2007-06-17
Please title your threads appropriately. Meaning the topic should correspond to your issue.

---

### Post by Lord Illidan on 2007-06-17
You can resize the XP partition, and install Ubuntu in the free space.

---

### Post by steveneddy on 2007-06-17
> **Lord Illidan said:**
> You can resize the XP partition, and install Ubuntu in the free space.

...by using the existing tool available in XP.

OR you could use a tool like Partition Magic which not only lets you resize your partitions in Windows, but you can assign them to be reformatted to Linux file systems before Linux installation.

I find that is is easier to partition BEFORE installation so the install disc sees the correct partition and you can choose the correct one to install to. This gives you the control of knowing how much, graphically, you are allocating to Linux.

Don't forget to partition a swap partition also.

---

### Post by Lord Illidan on 2007-06-17
> **steveneddy said:**
> ...by using the existing tool available in XP.

OR you could use a tool like Partition Magic which not only lets you resize your partitions in Windows, but you can assign them to be reformatted to Linux file systems before Linux installation.

I find that is is easier to partition BEFORE installation so the install disc sees the correct partition and you can choose the correct one to install to. This gives you the control of knowing how much, graphically, you are allocating to Linux.

Don't forget to partition a swap partition also.

Hmm.. I always used gparted, available in the installation to resize ntfs partitions.

---

### Post by Reily on 2007-06-17
> **MetalMusicAddict said:**
> Please title your threads appropriately. Meaning the topic should correspond to your issue.

Whoops. Sorry. :( OK, I'll consider installing Ubuntu. Thank you very much guys.

---

### Post by steveneddy on 2007-06-17
That would be excellent.....

---

### Post by Detonate on 2007-06-17
Before you start, to avoid problems resizing the XP partition, run a full defrag on the drive, preferably from "Safe Mode".

---

### Post by HermanAB on 2007-06-17
Howdy,

Linux generally plays nice in groups.  Unlike software by some other large company, Linux developers try not to trash the work of others.  All modern Linux distributions will check how much room is available on disk, create a separate partition for Linux and install a boot loader that will allow you to choose what system you want to run at start-up.  The partitioning tools of Linux are very good - I haven't had trouble partitioning Windows systems in the last 5 years.

Cheers,

Herman

---

