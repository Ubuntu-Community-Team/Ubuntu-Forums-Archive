---
title: "unistaling"
date: 2008-12-25
forum: General Help
---

### Post by hezy00 on 2008-12-25
hello,
How can I uninstall the 7.10 ver. from HD? Where can I get live cd? Can I create it from the system? Is the instalation bootable disk abale to unistall? 
hezy.

---

### Post by ajcham on 2008-12-25
> **hezy00 said:**
> hello,
How can I uninstall the 7.10 ver. from HD? Where can I get live cd? Can I create it from the system? Is the instalation bootable disk abele to unistall? 
hezy.

For what purpose are you uninstalling?  If you intend to install another OS, then you can wipe the drive as part of that process.

If you want to make the drive available as a data-only partition you can use the gparted tool on a live disc - you can download the disk image from the [Ubuntu website]("http://www.ubuntu.com/getubuntu/download").

---

### Post by wolfen69 on 2008-12-25
no need to wipe it first. just install whatever OS you want over it.

---

### Post by hezy00 on 2008-12-26
I don't install other os, there's a newer ver. of ubuntu on the HD.

---

### Post by cariboo on 2008-12-26
If you have a later version of Ubuntu installed, I would suggest installing gparted, it is in the repositories,  once installed go to System-->Administration-->Partition Editor, deleted the partitions that 7.10 is installed on  then create a new partition and format it using whatever file system you want. You can get a LiveCD shipped to you for free [here]("https://shipit.ubuntu.com/"), or you can download the iso [here]("http://www.ubuntu.com/getubuntu/download").

Jim

---

