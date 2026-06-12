---
title: "How to backup/restore custom icons ?"
date: 2009-05-29
forum: General Help
---

### Post by ActiveFrost on 2009-05-29
```
dainis@suncore:/usr/share/icons/oxygen$ ls -l
total 44
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 128x128
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 16x16
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 22x22
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 32x32
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 48x48
drwxr-xr-x 14 root root  4096 2009-05-29 20:34 64x64
drwxr-xr-x  3 root root  4096 2009-05-29 20:34 8x8
-rw-r--r--  1 root root 12233 2009-04-01 20:48 index.theme
drwxr-xr-x  3 root root  4096 2009-05-29 20:34 scalable
```

Oxygen icon pack comes with Amarok, but - I want to backup them ( so I could use them without installing Amarok ).
Can I put all these directories/files into a zip archive ( and if I would want to restore them, I would extract them to a folder called oxygen ( located in /usr/share/icons/ ) ) ?

What would be the best way to get this done ?

---

### Post by HuckleSmothered on 2009-05-29
You don't have to back them up at all. It is a normal package in Ubuntu. Just install the package: kde-icons-oxygen. This will install the full icon set, like you are showing there. Which is then selectable when you go through Appearance to change your icon theme.

---

### Post by ActiveFrost on 2009-05-30
> **HuckleSmothered said:**
> You don't have to back them up at all. It is a normal package in Ubuntu. Just install the package: kde-icons-oxygen. This will install the full icon set, like you are showing there. Which is then selectable when you go through Appearance to change your icon theme.

Thanks a million ( wasn't able to find it by myself :( ) !

---

