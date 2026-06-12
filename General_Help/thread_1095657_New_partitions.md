---
title: "New partitions?"
date: 2009-03-14
forum: General Help
---

### Post by ben140 on 2009-03-14
hi. I need to create(or format) a partition in NTFS for windows vista. but i dont know how, someone please give me a super noob guide to doing this...if u do u get a :KS!

---

### Post by theozzlives on 2009-03-14
Use partition  Editor from the Live CD.

---

### Post by nelskurian on 2009-03-14
If you want to access your Ubuntu partition(s) in windows, you need to use fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

And if you want to access windows while you are in Ubuntu, install ntfs-config use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
Code:

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

