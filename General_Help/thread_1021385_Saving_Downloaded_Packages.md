---
title: "Saving Downloaded Packages"
date: 2008-12-25
forum: General Help
---

### Post by Tramx on 2008-12-25
Hi, I'm new to Linux and Ubuntu. I download & install packages by Add/Remove Applications and I was wondering if there was a way to save the packages I downloaded as a file so I wouldn't have to connect to Internet when I need to reinstall the packages or make a clean re-installation of Ubuntu...

---

### Post by taurus on 2008-12-25
The apps that you installed will be saved to /var/cache/apt/archives _unless_ you clean the cache first.

Applications -> Accessories -> Terminal
```
ls -la /var/cache/apt/archives
```

---

### Post by Tramx on 2008-12-25
Thank you, I found it.:)

---

