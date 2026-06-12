---
title: "Error when installing packages"
date: 2006-01-01
forum: General Help
---

### Post by Bachstelze on 2006-01-01
```
E: /var/cache/apt/archives/samba_3.0.14a-6ubuntu1_i386.deb: failed in buffer_read(fd)
```

I get this when using either Synaptic, apt-get or dpkg -i and for all packages. Any ideas ?

---

### Post by sciurus on 2006-01-02
sudo rm /var/cache/apt/archives/samba_3.0.14a-6ubuntu1_i386.deb

---

