---
title: "[SOLVED] Samba / Hard Drives Problems"
date: 2009-01-12
forum: General Help
---

### Post by tanha on 2009-01-12
Hello,

I'm trying to set up a share on one of my partitions on /dev/hdb; it doesn't work. When I create a share on /home partion on /dev/hda it works. Any ideas why on one and not the other?

Thanks.

---

### Post by electrogeist on 2009-01-12
Maybe a stupid question so sorry, but the way you called /home a partition on /dev/sda I thought I'd ask...

You do have /dev/sdb mounted somewhere right?

Then take a look at permissions

---

### Post by tanha on 2009-01-12
> **electrogeist said:**
> Maybe a stupid question so sorry, but the way you called /home a partition on /dev/sda I thought I'd ask...

You do have /dev/sdb mounted somewhere right?

Then take a look at permissions

/dev/sdb is partitioned as /dev/sdb1, /dev/sdb2..., which are all mounted in different directories, as specified in /etc/fstab. I own all the directories, etc., no problem with the permissions.

This is the exact error I get:

Unable to mount location
Failed to mount Windows share


----------------
Solved
Turns out my permissions were to tight (700). I added rx for the folder and now it's good. Thanks for the suggestion, electrogeist.

---

