---
title: "not recognizing IDE Hard disk"
date: 2009-04-21
forum: General Help
---

### Post by maldini83 on 2009-04-21
When I installed Ubuntu, it recognized my hda1 and hda3 (which are Win XP partitions) so I can access them from Ubuntu.

When I wanted to install Xubuntu, in the installation process I saw sda1 and sda3 instead of hda1 and hda3, so now I can't access these partitions from Xubutnu.

For some reason Xubuntu recognized my IDE drives as SCSI !!!

Why is that ? and how can I see my XP partitions from Xubutnu ?

Thanks.

---

### Post by bzr on 2009-08-12
I'm having a similar problem. I installed 3 hds and a cd-rom on an old AMD box. Primary IDE has CD-Rom as Master and 40 Gb HD as slave, where I was able to install 8.04 on the primary slave. I have 2 more 40 Gb HDs on the secondary IDE channel but Ubuntu doesn't recognize them to either partition or mount, it sees one of them as a SCSI drive. I'm trying to make this box somewhat of an NAS but without access to the other two drives, it's just a toybox for now. 

Any help would be greatly appreciated!!



[COLOR=Red]Oh, what a maroon I am! Instead of physically checking the connection, I just followed with my eye and assumed the HD was on the slave on the second IDE channel. When I finally followed the connection, it was going to the second connector on the floppy ribbon!!! Got everything straightened out and now have 3 drives to work with.

If anything, I just bumped this issue for you, maldini![/COLOR]

---

