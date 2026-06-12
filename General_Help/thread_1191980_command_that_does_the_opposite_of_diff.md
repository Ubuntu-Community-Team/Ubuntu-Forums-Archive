---
title: "command that does the opposite of diff"
date: 2009-06-19
forum: General Help
---

### Post by shortridge11 on 2009-06-19
I have 2 folders with certain files.  These files take up space, and there are a large amount of them in both folders.  Going through them manually would take forever, so is there a command or flag for diff that i don't understand that can output any folders or files that are in both folders? I don't need recursive check, just in the top level of the 2 folders.  I tried man diff, but couldn't come up with anything.

---

### Post by geirha on 2009-06-19
How about this?
```

LANG=C diff -qs dir1/ dir2/
LANG=C diff -qs dir1/ dir2/ | grep identical$

```

---

### Post by shortridge11 on 2009-06-19
that didn't work. i put 2 folders with the same name in for testing purposes, and nothing was outputed

---

### Post by t0p on 2009-06-19
There is a program called **uniq** that can report or omit repeated lines in a file.  Check out its man page, maybe you can make it report repeated filenames in a directory.

---

### Post by geirha on 2009-06-19
Ah, well diff only compares the content of files. To find files and folders with the same name, you could try find like this:
```
cd dir1
find . -exec test -e /path/to/dir2/{} \; -print

```

---

### Post by shortridge11 on 2009-06-20
> **geirha said:**
> Ah, well diff only compares the content of files. To find files and folders with the same name, you could try find like this:
```
cd dir1
find . -exec test -e /path/to/dir2/{} \; -print

```

that worked and it also did the sub directories. is there a way to not do the sub directories?

---

### Post by geirha on 2009-06-20
> **shortridge11 said:**
> that worked and it also did the sub directories. is there a way to not do the sub directories?

Yes, with find's -maxdepth option
```

cd dir1; find . -maxdepth 1 -exec test -e /path/to/dir2/{} \; -print

```

---

### Post by shortridge11 on 2009-06-20
that is awesome, that worked amazingly, thanks a lot! =D

---

