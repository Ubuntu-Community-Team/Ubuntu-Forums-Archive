---
title: "where can i find vmlinuz source"
date: 2008-02-28
forum: Dell  Ubuntu Support
---

### Post by provisional_idiot on 2008-02-28
so im looking for the source of the kernel that came with my dell 1420:

vmlinuz-2.6.20-16-generic

---

### Post by mrsteveman1 on 2008-02-28
You should be able to install the source for that specific kernel by doing:
```

sudo apt-get install linux-source
```

Once you do that you should have the archive in /usr/src

you can then unpack the archive or do whatever you need to with it

---

