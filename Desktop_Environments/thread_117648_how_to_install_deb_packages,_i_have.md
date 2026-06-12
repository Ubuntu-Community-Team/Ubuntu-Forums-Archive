---
title: "how to install deb packages, i have ?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by vidyaraj on 2006-01-15
hi...

i have recently installed "Ubuntu 5.10 - Breezy Badger".

i need to install some debian packages that i have with me...i tried copying those debian packages into /var/cache/apt/archives....now what should i do to get them installed.

apt-get install is not working for those deb packages...

---

### Post by Perfect Storm on 2006-01-15
```
sudo dpkg -i XXXXXXXXXX.deb
```

---

