---
title: "A bug with the &quot;cd&quot; command?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by Somenoob on 2006-07-08
Folders with space between two words in their names, cannot be a current directory for some reason.

```
mern@mern:~$ cd /home/mern/Perl Programs
bash: cd: /home/mern/Perl: No such file or directory

```

That directory is present in my home directory, and I just get this output.

---

### Post by konst88 on 2006-07-08
write: cd "/home/mern/Perl Programs"

---

### Post by aysiu on 2006-07-08
Or type ```
cd /home/mern/P
``` and then hit the **Tab** key twice.

---

### Post by tonyr on 2006-07-08
My 2 cents:
precede spaces with a backslash, as in:
```

mern@mern:~$ cd /home/mern/Perl\ Programs

```
which is what **asyiu**'s suggestion produces.

---

### Post by Somenoob on 2006-07-08
Thanks :D

---

