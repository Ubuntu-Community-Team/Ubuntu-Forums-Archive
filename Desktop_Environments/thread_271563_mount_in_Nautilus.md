---
title: "mount in Nautilus"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Branta on 2006-10-04
**/etc/pmount.allow** has these _**XP NTFS**_ _partitions_:
```
/dev/hdb1
/dev/hdb2
/dev/hdb3
/dev/hdb5
/dev/hdb6
/dev/hdb7
```

I use /dev/hdb7 for 'Back Up' & this works fine:
```
sudo rsync -av /home/bob /media/Back\ Up/

```

When I use **Places**>**Computer**>**Back Up** I cannot enter the parition until I _**Right Click**_, _**Mount Volume**_, _**Terminate**_ and _**Restart Nautilus**_.

I **always have access** when I execute the **rsync** _above_.

**How do I get Nautilus to _[SIZE="4"]Remember[/SIZE]_ 'Back Up' is mounted?**


--- Bob ---

---

