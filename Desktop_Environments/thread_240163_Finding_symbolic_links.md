---
title: "Finding symbolic links"
date: 2006-08-20
forum: Desktop Environments
---

### Post by bobpaul on 2006-08-20
As I was running out of space on 1 file system I temporarily allowed the system to become a mess of symbolic links to files on other files systems. I'd now link to clean it up but would like to do so with the least work possible.

what I want to do is use something like *find* on the file system, but matching ONLY symbolic links. Preferably I'd like to find the file/folder linked to, but I can easily script that if I can get a list of the sybolic links that exist.

Any ideas?

---

### Post by llamakc on 2006-08-20
-type l is the flag for symlinks in the command `find`.

I think this will work:

find / -type l -print

Somebody brighter should give you precisely what you need. HTH.

---

### Post by llamakc on 2006-08-20
So something like

```

 sudo find / -type l -print | xargs ls -lh

```

Would work.

---

