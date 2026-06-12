---
title: "cli: directory mirror"
date: 2009-04-11
forum: General Help
---

### Post by r0b0h0b0 on 2009-04-11
Hi all. I need to maintain a mirror copy (b) of a directory structure (a). The following must take place (assuming the dir structures don't change):


- copy all new files from a to b (/a/1/01/file --> /b/1/01/file
- overwrite copy all changed files a to b
- delete from b files removed from a
- do this for all files in all subdirectories, but ignore (skip) for directories starting with "xyz"

any cli guru's out there willing to share some wisdom?

---

### Post by hyper_ch on 2009-04-11
have a look at rsync

---

### Post by KeyserSoze93 on 2009-04-11
> **r0b0h0b0 said:**
> Hi all. I need to maintain a mirror copy (b) of a directory structure (a). The following must take place (assuming the dir structures don't change):


- copy all new files from a to b (/a/1/01/file --> /b/1/01/file
- overwrite copy all changed files a to b
- delete from b files removed from a
- do this for all files in all subdirectories, but ignore (skip) for directories starting with "xyz"

any cli guru's out there willing to share some wisdom?

```
rsync -av /home/user/a --delete --exclude 'xyz*' /home/user/b
```

---

### Post by r0b0h0b0 on 2009-04-11
Yup, that's the one. In fact, **man rsync** tells me it's quite versatile.

---

