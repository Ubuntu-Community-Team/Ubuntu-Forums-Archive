---
title: "less free space than available"
date: 2009-06-25
forum: General Help
---

### Post by styleruk on 2009-06-25
Here's an odd one.  Why, when I open system monitor, does it show that I have 3.4GB more free than I do available.  Recently I ran out of space and it was showing that I had 2GB free and none available,  I have freed some up now and it shows that I have 33.4GB free and 30GB available?

Si

---

### Post by niteshifter on 2009-06-25
Hi,

Assuming a default install (ext3 file system) 5% of the total disk space is reserved. This is done so that the root user has some space to work with.

---

### Post by yota on 2009-06-25
eventually the reserved space size can be tuned with
```

tune2fs -r <percent> <partition>

```

hope this help

---

