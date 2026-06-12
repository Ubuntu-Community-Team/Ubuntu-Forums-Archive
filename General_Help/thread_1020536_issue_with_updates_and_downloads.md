---
title: "issue with updates and downloads"
date: 2008-12-24
forum: General Help
---

### Post by 4me on 2008-12-24
i was doing the updates from a hotel room and for whatever reason it 'stopped' or was 'taking too long'.  so i stopped the updates.

now i get this when i attempt to use the update manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


obviously i am no genius, but i went to the terminal to do the 'quoted' part and it said must have superuser privalages.

i am sure there is a simple solution here.   thank you in advance.

4me

---

### Post by redilyn on 2008-12-24
You need to do the following

```

sudo dpkg --configure -a

```

---

### Post by taurus on 2008-12-24
More about "superuser" or sudo as we call it around here.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

