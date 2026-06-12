---
title: "recursive file renaming"
date: 2009-01-29
forum: General Help
---

### Post by steavy on 2009-01-29
I want to make a recursive file renaiming. 

For example I need to rename all files in /home/user to the file name with a .txt at the end. A file "test.mp3" will be "test.mp3.txt" and "hello.txt" will be "hello.txt.txt".

Also I need a terminal command to rename them back removing the .txt I just added. :D

I know it sounds rare but I need some help to do this. I appreciate any ideas.

Thanks

---

### Post by kaibob on 2009-01-29
The following will do what you want:

```
find /directory/name -type f -exec rename -n 's/$/.txt/' '{}' ';'
```

The -n option directs rename to do a dry run and report proposed changes; substitute -v for -n to actually rename the files.

To reverse the changes:

```
find /directory/name -type f -exec rename -n 's/.txt$//' '{}' ';'
```

---

### Post by steavy on 2009-01-29
Thanks a lot kaibob it worked great! :D

---

