---
title: "Copying folders between users"
date: 2009-06-22
forum: General Help
---

### Post by The Switch Blade on 2009-06-22
root@earl-desktop:/iraf/xdimsum# cp /home/earl/Desktop/xdimsum/* .
cp: omitting directory `/home/earl/Desktop/xdimsum/bin'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.alpha'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.generic'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.linux'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.macosx'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.redhat'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.sparc'
cp: omitting directory `/home/earl/Desktop/xdimsum/bin.ssun'
cp: omitting directory `/home/earl/Desktop/xdimsum/demos'
cp: omitting directory `/home/earl/Desktop/xdimsum/doc'
cp: omitting directory `/home/earl/Desktop/xdimsum/lib'
cp: omitting directory `/home/earl/Desktop/xdimsum/redhat'
cp: omitting directory `/home/earl/Desktop/xdimsum/src'

Why can't I copy a folder from one user to another?

---

### Post by mikewu on 2009-06-22
Add the -r flag to copy folders.
```
cp -r /home/earl/Desktop/xdimsum/* .
```

Also remember that the new files will be owned by root.
Change the owner with 
chown -R NEW_USER .

---

### Post by The Switch Blade on 2009-06-22
Thanks. When I chown, why does it only change one of the permissions? i.e.

-rw-r--r-- 1** iraf root**   109 2009-06-22 16:32 xdimsum.par

---

### Post by mikewu on 2009-06-22
In -rw-r--r-- 1 iraf root 109 2009-06-22 16:32 xdimsum.par
iraf is the owner and root is the group. 

Thus you have to change the group that owns the file aswell. 
```
sudo chgrp -R iraf .
```
should change the groups to the correct setting.

---

