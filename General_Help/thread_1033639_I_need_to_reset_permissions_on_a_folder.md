---
title: "I need to reset permissions on a folder"
date: 2009-01-07
forum: General Help
---

### Post by memories on 2009-01-07
I have a folder which has 777 for every single file/directory. I would like to set my default umask to each file/folder in the directory, recursively. I'm pretty sure there's no way to do this without writing a small script.. or is there?

---

### Post by marshall.robert on 2009-01-07
simple

```

chmod -R 777 /path/to/dir

```

make sure its -R not -r

---

