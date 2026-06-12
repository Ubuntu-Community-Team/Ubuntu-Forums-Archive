---
title: "Permissions"
date: 2005-03-07
forum: Desktop Environments
---

### Post by javamdk on 2005-03-07
Hey guys:
 I just transferred over files from my CD to my linux home directory. The only problem now is each file and folder contains a lock on it so they cannot be modified but just viewed. The files go like this:

 [HTML]My Doc
|_Subfolder (lock)
|_Subfolder (lock)
   |_file (lock)
   |_file (lock)[/HTML]

How can I change My Doc and all its files and subfolders to 775?

Thanks

---

### Post by burlap on 2005-03-07
```
chmod -R 775 /path/to/My Doc
```

---

### Post by javamdk on 2005-03-07
fantastic... thank you!

---

