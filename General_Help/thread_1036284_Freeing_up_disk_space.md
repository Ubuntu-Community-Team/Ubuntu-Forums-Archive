---
title: "Freeing up disk space"
date: 2009-01-10
forum: General Help
---

### Post by Hangwire on 2009-01-10
How can I free up more disk space. I deleted all my garbage, etc. Any other way? I read something about deleting the archives from the updates, how is that done?

---

### Post by taurus on 2009-01-10
```
sudo apt-get clean
sudo apt-get autoremove
df -h
```
Don't forget to empty your trash bin too.

---

