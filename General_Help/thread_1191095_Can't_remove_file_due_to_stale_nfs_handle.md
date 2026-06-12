---
title: "Can't remove file due to stale nfs handle?"
date: 2009-06-18
forum: General Help
---

### Post by Kreuger on 2009-06-18
Whenever I try to delete this folder it gives me an error saying that there's a rar file inside with a stale nfs handle. However there's nothing visible inside the folder even with hidden files showing. I tried to do rm -rf and it said the same thing.

---

### Post by MyR on 2009-06-18
does a
```
ls -a
```
show anything in the directory?

I would unofficially recommend sticking a sudo in front of the rm.  But don't erase your drive with it etc. etc.

peace

---

### Post by Kreuger on 2009-06-18
Oddly enough the file does show that way and I never thought to check that. But using sudo did nothing..

---

### Post by nandemonai on 2009-06-18
Unmount the NFS share? Or are you trying to remove something on a share? Stale share means the NFS server has gone down and not come up again nicely.

---

### Post by WiseMaturin on 2009-08-17
> **nandemonai said:**
> Unmount the NFS share? Or are you trying to remove something on a share? Stale share means the NFS server has gone down and not come up again nicely.

How would one go about doing that?

---

### Post by nandemonai on 2009-08-17
> **WiseMaturin said:**
> How would one go about doing that?

```
sudo umount /mount/point/
```

Then remount the share and all should be well. This is assuming that the NFS server is functioning ok.

---

