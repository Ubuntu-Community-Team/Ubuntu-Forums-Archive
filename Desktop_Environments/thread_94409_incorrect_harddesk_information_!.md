---
title: "incorrect harddesk information !"
date: 2005-11-23
forum: Desktop Environments
---

### Post by fahad on 2005-11-23
Hi all,

i have 120 HDD,
and iam sure that i used a little gigs "4.6Gib" of it, "right click->properties in / folder"

but the system monitor and "df -h " tells me Not ! "60Gib" used !!

who will i believe :p ?,
Really i want to know how much free gigs i have,and i want the df command or system monitor tells me correctly the size of the free gigs and to be approx. the same as  "right click->properties in / folder"

-
see the attachments

---

### Post by RAOF on 2005-11-24
Notice the "some contents unreadable" part of the properties for the / directory.  It hasn't counted everything on your partition in that 4.6 GB.  All three of those screenshots agree that you've got about 40 GB free.  If you are absolutely certain you **haven't** got ~60 GB of stuff on that partition, it's possible that the filesystem has been damaged in some way, and you should run fsck on it (from a livecd, because you can't repair your root partition while it's being used ;))

---

### Post by fahad on 2005-11-24
i just installed ubuntu from 5 hours ago :p
-
i will run fsck in acouple of hours....

---

### Post by fahad on 2005-11-24
OOps,

i found out why there is  small free space in my HDD, while iam sure that i have much free space,

Reason:
i didnot clean up my trash :rolleyes: 

now every things make sense
:p

---

