---
title: "update problem"
date: 2009-02-14
forum: General Help
---

### Post by adult swim on 2009-02-14
i have messed up my install some im chrooting into it from a live cd.  for some reason whenever i try to apt-get update, i get the error ```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
``` for every entry in my sources.list.  i have tested my internet connection, i can ping things and i can even update the live cd install.  i have tried copying the live cd sources.list to the install im chrooting and updating but i still get the same errors about not being able to resolve archive.ubuntu.com.  does anyone know what im doing wrong here?

---

### Post by dcstar on 2009-02-14
> **adult swim said:**
> i have messed up my install some im chrooting into it from a live cd.  for some reason whenever i try to apt-get update, i get the error ```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
``` for every entry in my sources.list.  i have tested my internet connection, i can ping things and i can even update the live cd install.  i have tried copying the live cd sources.list to the install im chrooting and updating but i still get the same errors about not being able to resolve archive.ubuntu.com.  does anyone know what im doing wrong here?

Select another repository mirror in System-Administration-Software Sources.

---

