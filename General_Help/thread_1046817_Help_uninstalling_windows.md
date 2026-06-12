---
title: "Help uninstalling windows"
date: 2009-01-21
forum: General Help
---

### Post by adoyle626 on 2009-01-21
I downloaded ubuntu about a month ago and I love it.
I don't use windows, and I wanted to know how I could take it off of my computer.
I googled it, but I need windows 98 or 2000 to do it, and I do not have the CDs.

I hope you can help me out,
Thanks

---

### Post by Crafty Kisses on 2009-01-21
Well once you put the Ubuntu LiveCD in and you select install, you could always select the **"Guided Partition: Use entire HD"** option, that will remove Windows and obviously install Ubuntu.

---

### Post by adoyle626 on 2009-01-21
If I do this will it uninstall ubuntu and reinstall it, but it will also take off windows?

Thanks a bunch for the fast and great answer. =)

---

### Post by Crafty Kisses on 2009-01-21
Oh I'm sorry I misread your post, you want to basically remove the Windows partition, gotcha! Sorry about that, can you just post the following output?
```
sudo fdisk -l
```
Then from there I or someone else can help you.

---

### Post by Trixilver on 2009-01-21
Partitioning the entire HDD will wipe EVERYTHING, so yes it will remove your current Ubuntu as well, but it will install a new Ubuntu afterwards.

---

