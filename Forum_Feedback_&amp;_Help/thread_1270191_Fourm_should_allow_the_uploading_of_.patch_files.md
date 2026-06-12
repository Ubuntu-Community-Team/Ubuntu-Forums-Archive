---
title: "Fourm should allow the uploading of .patch files"
date: 2009-09-19
forum: Forum Feedback &amp; Help
---

### Post by ode on 2009-09-19
Hi,

.patch should be added to the filetypes that are allowed to be uploaded and attached to posts.
Having to compress the file adds an additional stage to the poster explaining the untar stage and the user having to carry it out.

Thanks

---

### Post by jpeddicord on 2009-09-19
> **ode said:**
> Hi,

.patch should be added to the filetypes that are allowed to be uploaded and attached to posts.
Having to compress the file adds an additional stage to the poster explaining the untar stage and the user having to carry it out.

Thanks

It would be a handy type to have added. You can also simply upload it as .txt; patch won't care.

Also, with a gzip-compressed patch, you can still apply it with a one-liner.

Instead of:```
patch -p1 < mypatch.patch
```You can use```
zcat mypatch.patch.gz | patch -p1
```to decompress and apply all at once.

---

