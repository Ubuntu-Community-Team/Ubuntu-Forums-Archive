---
title: "USB Disk and FSTAB"
date: 2009-04-09
forum: General Help
---

### Post by measekite on 2009-04-09
I have an external USB2 Drive formatted for NTFS so I can also access it from Windows.

There is [COLOR=Red]no entry in FSTAB[/COLOR].  

**Should there be an FSTAB entry?**

I also have an EIDE Drive formatted for NTFS (same reason) and there [COLOR=Red]is an FSTAB entry[/COLOR].

**Why is one required for FSTAB and not for USB?**

---

### Post by vanadium on 2009-04-09
External, removable drives by default are automatically mounted when you insert them. The "old" mechanism using fstab is not used for these drives. Thus, *there should not be an entry*.

In current ubuntu versions, non system partitions are *not* automatically mounted: they are only mounted "on demand", i.e. when you click them in nautilus.

That you have an entry without you knowing to have put it in suggests to me that either you are using an older Ubuntu version, or you have upgraded your system each time. Older versions of ubuntu included non-system partitions in /etc/fstab at install time.

---

### Post by measekite on 2009-04-09
Thanks

---

