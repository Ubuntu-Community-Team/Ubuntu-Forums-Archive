---
title: "How to use dd to copy DVD"
date: 2012-01-29
forum: Desktop Environments
---

### Post by borgward on 2012-01-29
How do I use dd to copy DVD?

---

### Post by amauk on 2012-01-29
Assuming your DVD device (input file) is /dev/sr0
and your output file is /home/username/dvd.iso
```
dd if=/dev/sr0 of=/home/username/dvd.iso
```

Just FYI
dd (data dump) will just copy something bit-for-bit
So if the DVDs encrypted or anything, the copy will be too

---

