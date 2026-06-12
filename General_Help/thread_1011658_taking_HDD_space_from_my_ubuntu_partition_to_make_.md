---
title: "taking HDD space from my ubuntu partition to make a new partition?"
date: 2008-12-15
forum: General Help
---

### Post by faceless-21 on 2008-12-15
hey guys I want to basically resize my linux partition.  Its 40gbish and I want to take 10ish off it and reformat it with my windows partition so as to make it larger...  Anyone have any ideas how I might go about that?

  Thanks

---

### Post by faceless-21 on 2008-12-16
anyone?

---

### Post by spcwingo on 2008-12-16
First:

```
sudo apt-get install gparted
```

Then go to system>admin>partition editor and just use the sliders to resize the partitions.

---

### Post by cdtech on 2008-12-16
Once you have the "gparted" installed, take a snapshot of the gparted screen (with your correct drive selected) so we can see the layout of your drive.

---

