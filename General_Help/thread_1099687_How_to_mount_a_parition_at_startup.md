---
title: "How to mount a parition at startup?"
date: 2009-03-18
forum: General Help
---

### Post by mahela007 on 2009-03-18
I want to mount my windows partitions automatically at start-up. How can I do this?

---

### Post by taurus on 2009-03-18
Install ntfs-config and use it to configure your ntfs partition, assuming it's a ntfs filesystem.

```
sudo apt-get update
sudo apt-get install ntfs-config
kdesu ntfs-config
```

---

### Post by 2hot6ft2 on 2009-03-18
Also
Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support for which ever it is (internal or external) and click OK. All done

Now it will auto mount with read/write support after you reboot.

---

