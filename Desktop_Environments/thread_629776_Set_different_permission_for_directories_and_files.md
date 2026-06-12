---
title: "Set different permission for directories and files"
date: 2007-12-02
forum: Desktop Environments
---

### Post by mmcmonster on 2007-12-02
I have two computers I'm keeping in sync using rsync.  My rsync command is:
```
rsync -avurtpogL --progress --delete usename@hostname:/home/shared/Pictures /home/shared/
```The problem is, on the destination computer, I would like all directories to be a+rx and all files to be a+r (so that all users on the destination computer can access all the directories and read all the files).  What is the best way to achieve this?

---

### Post by njparton on 2007-12-02
I can't think of a way of using chmod on files OR directories & not both at the same time.

Try ```
man chmod
``` to see if there are any switches available for doing this.

---

### Post by mmcmonster on 2007-12-02
I tried ***man chmod***.  It was exceptionally unhelpful and unusually terse.  Maybe someone who knows how to script can write a short thing out for me?

---

### Post by mmcmonster on 2007-12-02
Found an answer for myself.
```
chmod -R a+r *
find -type d -exec chmod go+rx '{}' \;

```These two commands will make all files in alll subdirectories readable and all subdirectories readable and executable.

---

