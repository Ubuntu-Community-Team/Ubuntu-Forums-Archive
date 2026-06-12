---
title: "[SOLVED] How to find what the permissions are on a file in the terminal"
date: 2009-01-11
forum: General Help
---

### Post by beattyml1 on 2009-01-11
So I want to change the permissions of a file using chown and chmod but I want to be able to put them back as I found them if I mess them up, so how do I find out the permissions for a file/folder in the terminal, both the owner/group and the read write permissions

---

### Post by Dr Small on 2009-01-11
Try:
```
ls -lah
```

---

### Post by hikaricore on 2009-01-11
> ls -la

Would do the trick, the h flag that Dr Small listed only makes the file sizes more readable, meaning 104857600 becomes 100M.

---

### Post by felker2 on 2009-01-11
> **Dr Small said:**
> Try:
```
ls -lah
```

I didn't know the -h option. Nice. Thanks.

---

