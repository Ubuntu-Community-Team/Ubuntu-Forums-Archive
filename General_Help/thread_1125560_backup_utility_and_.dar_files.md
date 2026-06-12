---
title: "backup utility and .dar files"
date: 2009-04-14
forum: General Help
---

### Post by bu2971x on 2009-04-14
I burned a backup using the home backup app. It makes a .dar file.
I tried to open the files on the dvd but it says doesnt have application to open them.  What do I need for that.??

---

### Post by cattlerepairman on 2009-04-27
HELP! Same problem! I backed up everything before doing a clean install of ubuntu 9.04 and now I am stuck without the program that I used to back up the /home folder. I have an archive.dar and a catalog.dar file and do not know what to do with them!

---

### Post by Christmas on 2009-04-27
It looks like DAR is an [archive format](http://dar.linux.free.fr/). Try installing the dar package:
```
sudo apt-get install dar
```
Then use it like:
```
dar -x archive_file.dar
```

---

