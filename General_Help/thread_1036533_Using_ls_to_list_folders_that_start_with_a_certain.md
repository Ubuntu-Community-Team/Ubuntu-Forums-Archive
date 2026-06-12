---
title: "Using ls to list folders that start with a certain string?"
date: 2009-01-10
forum: General Help
---

### Post by brawnyman713 on 2009-01-10
```

ls 5*

```
I thought this command would list every file and folder that starts with a 5. However, this takes the one result that shows up (a folder) and prints the contents of that folder. How would I have it list all (in this case, one) folders in the working directory that start with a 5?

---

### Post by chex_m8 on 2009-01-10
ls | grep 5

---

### Post by tuxxy on 2009-01-10
> **brawnyman713 said:**
> ```

ls 5*

```I thought this command would list every file and folder that starts with a 5. However, this takes the one result that shows up (a folder) and prints the contents of that folder. How would I have it list all (in this case, one) folders in the working directory that start with a 5?

You could use the find tool also;

```
find /home/user/Desktop -name '5*'
```

---

### Post by brawnyman713 on 2009-01-10
Thanks, tuxxy. That's perfect

Edit: I tried running it, and unfortunately it also displayed a whole bunch of files that start with five inside of some of the directories. Is there some way to have it only search one directory deep?

---

### Post by tuxxy on 2009-01-10
No problem, glad it worked :)

---

### Post by brawnyman713 on 2009-01-10
Actually, it works, but it displays a bunch of files that start with a five on folders deeper down. Is there some way to have it search only one directory deep?

---

### Post by heindsight on 2009-01-11
try doing
```
ls -d 5*
```

this will list everything in the current directory that starts with 5

the -d option to ls ensures if any directory name starts with 5 it will not list the directory contents.

---

