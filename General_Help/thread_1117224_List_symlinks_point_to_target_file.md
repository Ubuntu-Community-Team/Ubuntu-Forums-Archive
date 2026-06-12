---
title: "List symlinks point to target file"
date: 2009-04-05
forum: General Help
---

### Post by napzilla on 2009-04-05
This seems like it should be a simple thing to do, and maybe I just have the dumb today. A long time ago, I created a symlink to a file. Now I'm looking at the file trying to remember where I created the symlink. Is there a converse to "ls -l" or "readlink" that will list the references pointing *to* a target file? I went through the manpages for ls and ln and couldn't find anything, nor did my handy "Linux Pocket Guide" have any insight to share. Any ideas?

Thanks!

---

### Post by napzilla on 2009-07-02
I resolved my issue without answering this question. Anybody know the magic command or flag?
:?:

---

### Post by Boondoklife on 2009-07-02
only thing i cud think of would be this
```
ls -l | grep "\-> /etc"

```

replacing the /etc with the location or file it pointed to.

---

### Post by johnkeates on 2009-08-05
Combine that with a find / I guess

---

### Post by Glyndwr on 2009-08-05
find / -type l

will give you all the symlinks on your system

---

### Post by Boondoklife on 2009-08-05
If you are looking to go through the entire file system then yes it would just add ls -lR / to the front of the command instead of ls -l.

---

### Post by malclocke on 2009-08-19
To find all symbolic links to the file /home/me/foo on the whole filesystem:
```

find / -lname /home/me/foo

```

---

### Post by jure.skelin on 2011-01-12
[http://ubuntuforums.org/showpost.php?p=504794&postcount=5](http://ubuntuforums.org/showpost.php?p=504794&postcount=5)

to exclude same paths (for example /dev and /sys)
```
find /!(dev|sys) -follow -inum <inode number>
```

---

