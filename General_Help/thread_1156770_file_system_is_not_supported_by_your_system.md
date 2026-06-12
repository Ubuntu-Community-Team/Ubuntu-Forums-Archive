---
title: "file system is not supported by your system"
date: 2009-05-12
forum: General Help
---

### Post by kuldeepsidhu on 2009-05-12
i am using windows xp and ubuntu 8.04.today i reinstalled the windows and after that when i again correct the boot loader by using the live cd.ubuntu is working correct after that but it is giving error when i try to mount ntfs drive..it says  "the volume SONGS uses the file system which is not supported by your system"..before installing windows it is mounting the same ntfs parition properly..what should i do..?i have noe make any changes to the parition..



Thanks in advance...

---

### Post by danwood76 on 2009-05-12
Errors can be caused if you didnt shut windows down correctly and the ntfs journal has extra data in it.

Try mounting from the command line and see what the error is.

If you dont know how to do that could you open up a terminal and post the output of the following commands?
```

sudo fdisk -l
cat /etc/fstab

```

---

