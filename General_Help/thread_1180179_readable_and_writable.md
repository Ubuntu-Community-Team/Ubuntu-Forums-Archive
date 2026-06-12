---
title: "readable and writable"
date: 2009-06-06
forum: General Help
---

### Post by lex1 on 2009-06-06
How to make nontmp file owned by www-data which i think it is but also and ONLY readable and writeable by www-data

total 8
drwxr-xr-x 2 root     root     4096 2009-06-06 16:42 .
drwxr-xr-x 6 root     root     4096 2009-06-06 16:24 ..
-rw-r--r-- 1 www-data www-data    0 2009-06-06 16:32 nontmp

lex1;)

---

### Post by michy99 on 2009-06-06
```
sudo chmod 600 nontmp
```

---

### Post by lex1 on 2009-06-06
thanks for your post

if i want to set permission of 
nontmp to 0x700 (-rwx------
what should I do?

lex1:p

---

### Post by markharding557 on 2009-06-06
there is a gui way of setting permissions in the properties tab in nautilus,you will probably need to run nautilus as root.
rightclick on your file and choose properties at the bottom and use the permissions tab.

---

