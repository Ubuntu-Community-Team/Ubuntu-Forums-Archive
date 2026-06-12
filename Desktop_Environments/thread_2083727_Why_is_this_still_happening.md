---
title: "Why is this still happening?"
date: 2012-11-13
forum: Desktop Environments
---

### Post by MakOwner on 2012-11-13
Again.  And Again.

<code> GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
</code>

---

### Post by dannyboy79 on 2012-11-13
try the following commands,
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
```
```
sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo aptitude update
```

---

