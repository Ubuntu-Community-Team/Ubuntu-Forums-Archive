---
title: "get this message when I try to install updates..."
date: 2008-01-12
forum: Desktop Environments
---

### Post by alanmzifa on 2008-01-12
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Can I ask why I'm getting this and what I need to do about it.

thanks


I'm on the latest Xubuntu release 7.10.

---

### Post by lluisanunez on 2008-01-12
Do what it says:
```
sudo dpkg --configure -a
```

---

### Post by alanmzifa on 2008-01-12
thanks. 

after a few stalled attempts all updates seem to be downloaded and installed,

---

