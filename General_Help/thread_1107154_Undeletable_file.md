---
title: "Undeletable file"
date: 2009-03-26
forum: General Help
---

### Post by c1rcu17 on 2009-03-26
I have a folder on my external hd that I can't seem to delete. How this folder got here, I have no idea.

ls -lah
```

*****@***********:/media/External$ ls -lah
total 172K
drwxrwxrwx 1 root root  12K 2009-03-26 13:13 .
drwxr-xr-x 5 root root 4.0K 2009-03-26 00:43 ..
drwxrwxrwx 1 root root 128K 2009-03-20 15:05 asdfas
drwxrwxrwx 1 root root    0 2009-03-26 13:13 Audio
drwxrwxrwx 1 root root 4.0K 2009-03-16 14:51 Backup
drwxrwxrwx 1 root root 8.0K 2009-02-17 18:30 Software
drwxrwxrwx 1 root root  16K 2009-03-21 15:49 Video

```

I'm trying to delete the asdfas folder. When I navigate inside of it and ls, I get.
```

ls: reading directory .: Input/output error

```

I can move the file anywhere within my external and can rename it.

sudo rm -r -f
```

rm: cannot remove directory `asdfas': Directory not empty

```

I can't delete it in window$ either. Any idea how to get rid of this folder?

---

### Post by Neo_The_User on 2009-03-26
sudo rm -rf --force

---

### Post by c1rcu17 on 2009-03-26
```
sudo rm -rf --force asdfas/
rm: cannot remove directory `asdfas': Directory not empty
```

---

### Post by Neo_The_User on 2009-03-26
unmount it first then delete.

---

### Post by c1rcu17 on 2009-03-26
Wait, if I unmount it, how do I delete the file?

---

### Post by regala on 2009-03-26
> **c1rcu17 said:**
> Wait, if I unmount it, how do I delete the file?

A file system is mounted ON the directory, so you cannot remove it without unmounting the filesystem on it.

---

### Post by musashixXX on 2009-03-26
I'm not sure if that's the case. run 'mount' from the command line and post the output.

---

