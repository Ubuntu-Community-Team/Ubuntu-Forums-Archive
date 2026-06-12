---
title: "I did everything for Steam but still cannot write on NTFS"
date: 2015-08-26
forum: Gaming &amp; Leisure
---

### Post by k-nirvana12 on 2015-08-26
Hi! Yesterday, I tried so hard to make Steam install games on NTFS. 
I added this line to /etc/fstab
```
UUID=7C6439376438F60C /media/windows ntfs-3g auto,users,permissions 0 0
```
My drive now seen as windows and has permissions for writing and reading
but when I try to create a Steam Library in it, Steam says

New Steam library folder must be on a filesystem mounted with execute permissions

Is there a way to solve this

---

### Post by ethan27 on 2015-09-01
First I'm a complete Noob at Linux but from my basic knowledge I believe you can't run linux on an NTFS to begin with but what do I know. Anyway for anybody else trying to solve this can we please get more information like OS and Terminal output?

---

### Post by ethan27 on 2015-09-02
Also are you an Administrator? You may not have permissions to write to disk. If you are I don't know what to say.

---

