---
title: "find lowercase filenames"
date: 2009-02-19
forum: General Help
---

### Post by porchrat on 2009-02-19
hi all this more of a scripting question than an ubuntu question, hopefully you can help.

I want to find all the files and directories under a certain directory structure (so it needs to be recursive) that have lower case names.

I know I could do it with something like this:

```
#!/bin/sh
find $1 -name a* > files.txt
find $1 -name b* >> files.txt
find $1 -name c* >> files.txt
find $1 -name d* >> files.txt
```

but that is going to take forever, is there a way to give the -name option a [a-z] instruction instead of having to write 26 individual lines and have it do 26 individual finds?

I also need to use a few special characters (as some files beginning with special characters), but I have resigned myself to adding those manually.

---

### Post by mikewu on 2009-02-19
Try

find . -regex "[^A-Z]+"

Basically it matches anything not in the set of uppercase letters

---

### Post by sisco311 on 2009-02-19
```
find . -name "[a-z]*"
```
or```
find . -name "[^A-Z]*"
```
also works.

---

### Post by heindsight on 2009-02-19
You can use something like:
```
find . -not -name "*[A-Z]*"
```
That will (recursively) find all files and directories under the current directory whose names do not contain any of the characters A-Z.

---

### Post by heindsight on 2009-02-19
> **sisco311 said:**
> ```
find . -name "[a-z]*"
```
or```
find . -name "[^A-Z]*"
```
also works.

Those will find files whose names start with a lowercase character or do not start with an uppercase character respectively, not quite the same as files with all lowercase names

---

### Post by heindsight on 2009-02-19
> **mikewu said:**
> Try

find . -regex "[^A-Z]+"

Basically it matches anything not in the set of uppercase letters

The problem with -regex is that it matches the whole path, not just the filename, so this won't find a file with all lowercase name if it's in a directory with an uppercase character in the name.

---

### Post by porchrat on 2009-02-19
Thanx everyone those are very useful.  Seems like I was already halfway there anyway.

I think I will use the ```
find . -not -name "*[A-Z]*"
``` mentioned by heindsight as that will do exactly what I need as it will also pull out anything containing special characters.

Thanks again everyone.

---

