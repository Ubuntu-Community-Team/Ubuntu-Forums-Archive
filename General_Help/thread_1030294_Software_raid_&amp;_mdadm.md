---
title: "Software raid &amp; mdadm"
date: 2009-01-04
forum: General Help
---

### Post by Braveheart1980 on 2009-01-04
I want to create a software linear raid between 2 and eventually more devices

I was wondering if this will work:


```
mdadm --create /dev/md0  --level=0 --raid-devices=2 **/home/george/Dowloads**  /dev/sdb1
```

Can I mount a disk to a disk folder which already has data without corrupting them ?
If yes is the above mentioned command correct?

---

### Post by fjgaude on 2009-01-04
Software linear? or strip which is raid0? If the latter, leave out the /home/george/Dowloads and put in both drives you wish to use:

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

or whatever the drive names are.

If you wish **linear** use that instead of the 0 in --level=.

[B]Whatever you do make sure you have backups for important data.
[/B]

---

