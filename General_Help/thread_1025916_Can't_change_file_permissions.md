---
title: "Can't change file permissions"
date: 2008-12-30
forum: General Help
---

### Post by god0fgod on 2008-12-30
I doubt my problem will ever get answered here - [http://ubuntuforums.org/showthread.php?t=1025572](http://ubuntuforums.org/showthread.php?t=1025572)

The problem is pretty much general stuff so here seems better.

Below sums up the problem:

```
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ sudo chmod 0775 control
matt@matt-desktop:~/Desktop/lINK TO MY DOCUMENTS/Linux stuff/Phython scripts/Guessing game/deb_dev/DEBIAN$ ls -l
total 1
-rwxrwxrwx 1 root root 387 2008-12-30 13:37 control
```

---

### Post by kidders on 2008-12-31
Hi there,

Can you post the output of **mount**?

---

### Post by pmooney78 on 2008-12-31
I'm just guessing here, but based on your pathname, I'm assuming that you're accessing data that's stored on a physical volume that's formatted with a Windows filesystem (because that pathname includes a folder called "link to My Documents"). If that's the case, then that's the basis of your problem: Windows partitions can be mounted in Linux, and you can read or write to them, but Windows filesystems don't support file ownership and permissions in the same way as Unix-style filesystems do. (That is, you can't change the permissions for the files because Windows filesystems don't keep track of file permissions. Linux just uses standard permissions for everything on Windows drives.)

If this is the case, you have at least two options:
1. Move your data to a native Linux filesystem (ext3, jfs, reiserfs, etc.).
2. You can change the file ownership that Linux assumes *for the entire partition* by changing the options in your /etc/fstab file.

---

