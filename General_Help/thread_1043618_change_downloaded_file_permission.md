---
title: "change downloaded file permission"
date: 2009-01-18
forum: General Help
---

### Post by Bob White on 2009-01-18
A downloaded programme is shown as owner **root**. How do I change owner of this programme to **user**. Tried logging in as root but no good. Ubuntu 8.04 Any help please. Newbie !!!
Bob

---

### Post by taurus on 2009-01-18
Make sure you are in the directory where that file is.  Then run

```
sudo chown user:user filename
ls -la
```

---

