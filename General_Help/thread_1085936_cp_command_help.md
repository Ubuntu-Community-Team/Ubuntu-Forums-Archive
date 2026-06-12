---
title: "cp command help"
date: 2009-03-03
forum: General Help
---

### Post by toddr on 2009-03-03
Hello all,
I was wondering how I could copy a directory and all its sub-directories (actually upgrading to a larger hard drive) from one to another? This is what I have done so far:
sudo cp -a /folderA /folderB

This worked fine with the acception that within folderB is a folder labeled FolderA and within that folder is all the contents. What I really wanted is all the contents of folderA to be copied into FolderB without folderA.

---

### Post by heindsight on 2009-03-03
I think the easiest way to achieve this is to use rsync:
```
rsync -a /folderA/ /folderB
```
Note that the / at the end of folderA is important. It tells rsync to copy the contents of folderA rather than folderA itself.

In other words, if you leave out that trailing / and do:
```
rsync -a /folderA /folderB
```
you'll end up with folderA and all it's contents under folderB (just as if you used cp).

---

### Post by ibuclaw on 2009-03-03
The commandline argument **-T** will be your solution
```
sudo cp -aT /folderA /folderB
```

Regards
Iain

---

### Post by K7522 on 2009-03-03
EDIT: tinivole answered it as I was entering it!

---

### Post by ibuclaw on 2009-03-03
> **K7522 said:**
> EDIT: tinivole answered it as I was entering it!
Kudos to you :popcorn:

Yeah ... btw K7522:
```
cp -a
```
Is exactly the same as
```
cp -d -p **-r**
```

Regards
Iain

---

### Post by heindsight on 2009-03-03
> **tinivole said:**
> The commandline argument **-T** will be your solution
```
sudo cp -aT /folderA /folderB
```

Regards
Iain

Ah, thanks. Much better than my idea :)

---

### Post by mhelmer on 2009-03-03
I will just throw this out there because i like to use this command for backup.

cp -Ruv /source /destination

- The R copies all sub directories and files.
- The u copies only when the source file is newer than the destination file(or when the destination is missing.
-The v is verbose and just outputs the current file being copied.

---

### Post by toddr on 2009-03-03
Thanks guys! In progress now.... may take some time. 120gb takes a while!

---

### Post by toddr on 2009-03-04
Worked like a charm! I used this:
sudo cp -aT /folderA /folderB
Maybe next time I'll throw in a -v so I can see what's going on.
Thanks again,
Todd

---

