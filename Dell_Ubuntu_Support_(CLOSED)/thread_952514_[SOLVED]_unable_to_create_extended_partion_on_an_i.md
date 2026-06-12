---
title: "[SOLVED] unable to create extended partion on an inspiron 1520"
date: 2008-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ahumin on 2008-10-19
Yes, I know :rolleyes:, another post on partitioning a dell laptop *but* I have not found any posts that directly address my problem.

Firstly I want to keep MediaDirect, I'm sure I'll have use for it. I have read that the restore partition is not really necessary because I have the cd, and putting grub on kills its (ctrl + f11 ?) shortcut anyway. I'm happy to leave the utils partition too, it's tiny. I don't want to dual boot with windoze because I don't think it deserves anything more than a virtual machine. Whatever programs don't have a gnome equal can make do with wine, and if that's too hard then they can sit in the sandbox where they can't cause trouble. I'll have to have a couple of virtual XPs for work purposes anyway.

What's bugging me is the partition layout, I'm assuming I have to have 4 partitions so pressing the MediaDirect button won't kill ubuntu. I was thinking I'd just change the restore partition to swap, and the os partition to linux then all would be well. Can anyone advise for or against the validtiy of this?

Ideally I'd just like leave everything as is except for the os partition which would I would change to an extended partition so I can play with multiple partitions in linux. I have booted up with the live cd but gparted refuses to let me convert the os partiion into an extended one (see attachement). It lets me delete the restore and os partitions fine. Why would this happen? MediaDirect is on an extended partition already, are two extended partitions technically impossible? Or is it just the version of gparted that comes on the hardy cd?

---

### Post by gbrainin on 2008-10-19
Yes, two extended partitions are not possible.  You can have a fairly large number of logical partitions within your extended partition, but of the four primary partitions, only one can be designated as extended.

---

### Post by ahumin on 2008-10-22
Thanks for that. Nasty Dell, as if they needed to put MD on an extended partition.

So then, does anyone know if my 2nd paragraph is right and will work?

---

### Post by ahumin on 2008-11-05
never mind, i just zeroed out the hdd with dd. maybe later i will look for a nice little linux distro for media only and do a repartition and the rmbr thing to make use of the old md button.

---

