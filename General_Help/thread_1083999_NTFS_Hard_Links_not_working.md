---
title: "NTFS Hard Links not working?"
date: 2009-03-01
forum: General Help
---

### Post by hopla on 2009-03-01
I was under the impression that NTFS supported hard links and they were also supported by ntfs-3g.

But apparently it doesn't:
```
X@X:/media/sda5 % ls -la A B
ls: cannot access A: No such file or directory
ls: cannot access B: No such file or directory
X@X:/media/sda5 % echo 'file A' > A
X@X:/media/sda5 % cat A
file A
X@X:/media/sda5 % cp -al A B
X@X:/media/sda5 % cat A
file A
X@X:/media/sda5 % cat B
file A
X@X:/media/sda5 % echo 'file B' > B
X@X:/media/sda5 % cat A B
file A
file B

```

While on / (ext3):
```
X@X:~ % ls -la A B
ls: cannot access A: No such file or directory
ls: cannot access B: No such file or directory
X@X:~ % echo 'file A' > A
X@X:~ % cat A
file A
X@X:~ % cp -al A B
X@X:~ % cat A
file A
X@X:~ % cat B
file A
X@X:~ % echo 'file B' > B
X@X:~ % cat A B
file B
file B

```

Mount status:
```
X@X:~ % mount | grep /media/sda5
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

I'm running 8.10 and I need hard links for rsnapshotting to an external USB disk (that I also want to share with XP and other computers). Right now rsnapshot works, but the "cp -al" part takes ages (because, I think, it's actually silently copying all the files instead of making hard links).

---

### Post by hopla on 2009-03-02
I had someone else test this and he got the same, wrong, results.

So I filed a bug report:
[https://bugs.launchpad.net/ubuntu/+bug/336762](https://bugs.launchpad.net/ubuntu/+bug/336762)

---

