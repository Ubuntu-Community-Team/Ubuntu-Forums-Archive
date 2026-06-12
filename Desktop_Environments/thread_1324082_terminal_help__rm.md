---
title: "terminal help ?? rm"
date: 2009-11-12
forum: Desktop Environments
---

### Post by kingaj on 2009-11-12
i need help with a command. lets say i use the locate command to find all files in a directory that ends with .zip. and i want to use the rm command to delete all those files that end with rm. how would i chain those commands together to make it possible.

---

### Post by mike998 on 2009-11-12
I would use the following
```
ls *.zip | grep more
```
This will allow you to list all the .zip files in a directory.  If you are SURE that you want to delete ALL .zip files in a directory, use the following command from within the correct direcotry:
```
rm *.zip
```
You can also use *rm.zip if I interpreted your post correctly.

---

### Post by sisco311 on 2009-11-12
I would use *find* and *trash* to find the files and move them to the trash. 

```
find /path/to/dir -type f -iname "*.zip" -exec trash '{}' \;
```

You can list the trash with the *list-trash* command and empty it with *empty-trash*.

You may have to install [trash-cli]("apt://trash-cli") first.

OR simply run:
```
find /path/to/dir -type f -iname "*.zip" -delete
```

NOTE: 

Always list the files before deleting them:
```
find /path/to/dir -type f -iname "*.zip"
```

BE CAREFUL!

---

