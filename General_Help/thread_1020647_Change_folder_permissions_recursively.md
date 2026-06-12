---
title: "Change folder permissions recursively?"
date: 2008-12-24
forum: General Help
---

### Post by crazyfuturamanoob on 2008-12-24
I want to give read/write access to a folder, and it's content.

I tried this but it doesn't work:
```

chmod +r+w -R foldername

```

Also running it as sudo doesn't work either.

The files still have a lock icon on them.

---

### Post by taurus on 2008-12-24
> **crazyfuturamanoob said:**
> I want to give read/write access to a folder, and it's content.


For group or world?

```
chmod -R 777 directory
```

---

### Post by crazyfuturamanoob on 2008-12-24
> **taurus said:**
> For group or world?

```
chmod -R 777 directory
```

What is group and what is world?

---

### Post by kbuel on 2008-12-24
if you do an:

ls -l

you will see somethign like this:

drwxr-xr-x 2 name name 4096 2008-12-24 16:12 myDir


d[rwx][r-x][r-x] is the permissions.  d is for directory.  The first rwx is for owner, the second rwx is for group, and the third rwx is for world.

---

