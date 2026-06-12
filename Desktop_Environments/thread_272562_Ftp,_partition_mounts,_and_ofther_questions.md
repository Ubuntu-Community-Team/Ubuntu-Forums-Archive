---
title: "Ftp, partition mounts, and ofther questions"
date: 2006-10-06
forum: Desktop Environments
---

### Post by lemonsCC on 2006-10-06
I successfully setup my box to dual boot windows and Dapper.  The setup I followed was:
[http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/")

I setup my partitions like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1044     8385898+   7  HPFS/NTFS
/dev/hda2            1045        3690    21253995    f  W95 Ext'd (LBA)
/dev/hda3   *        3691        4865     9438187+  83  Linux
/dev/hda5            1045        2219     9438156    c  W95 FAT32 (LBA)
/dev/hda6            2220        3524    10482381   83  Linux
/dev/hda7            3525        3690     1333363+  82  Linux swap / Solaris

```

hda5 is accessable and writable on both Ubuntu and Windows.  This is great for when I need to swap file between the two, however it mounts as "_PNG."  Is there any way to have it mount in ubuntu as "Shared" or something similar?
[LIST]
[*]Is there any way to have it mount in ubuntu as "Shared" or something similar?
[*]Is there anyway to not have the hda1 (contains windows) mount at all?
[*]Is there anyway to SECURELY allow access to hda5 from the internet (such as file storage I can access at school)?
[/LIST]

---

### Post by lemonsCC on 2006-10-06
See next post

---

### Post by lemonsCC on 2006-10-06
1) Change the partition label in windows and it will show in Ubuntu
2) Remove hda1 from fstab and it wont mount (DUH!)
3) Umm??

---

