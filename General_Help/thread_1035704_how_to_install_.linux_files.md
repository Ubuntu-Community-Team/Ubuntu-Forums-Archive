---
title: "how to install .linux files ?"
date: 2009-01-10
forum: General Help
---

### Post by markg48 on 2009-01-10
going to download some large files that are in .linux format 
 but i dont no how you install these files i dont want to down load
a large file and cant use it :/

---

### Post by heindsight on 2009-01-10
I don't think the .linux indicates any particular file format. What exactly are you trying to download?

---

### Post by hyperdude111 on 2009-01-10
.linux?

They might be executable text files in which case go to their properties make them executable the run them as normal and select open in terminal.

The only files i thaught you colud install were
.deb
.rpm
.yum
.sh
.txt
.tar.gz
and .exe with wine

I never heard of a .linux file but good luck

---

### Post by markg48 on 2009-01-10
a private beta game that is available for linux windows  and mac the download is .linux

---

### Post by markg48 on 2009-01-10
ill go try it after i re install ubuntu coz windows deleated it >.<

---

### Post by heindsight on 2009-01-10
> **markg48 said:**
> a private beta game that is available for linux windows  and mac the download is .linux

In that case, I would guess it's either a binary executable or a shell script. Once you've downloaded it, open a terminal, cd to the directory where you saved the file and do 
```
chmod +x filename.linux
./filename.linux
```

---

### Post by binbash on 2009-01-10
there is no extension called .linux . Try using heindsight's way.

---

### Post by albinootje on 2009-01-10
> **markg48 said:**
> going to download some large files that are in .linux format 
 but i dont no how you install these files i dont want to down load
a large file and cant use it :/

You should simply find out where the installation instructions are.
Perhaps you will need to do :
```

chmod +x file.linux
sh ./file.linux

```
But again, find out how to install from the website you're downloading it from.

---

### Post by snova on 2009-01-10
Linux doesn't use file extensions to denote file type; at the least, it doesn't depend on them.

More than likely, the .linux extension is used simply to tell it apart from the Mac and Windows builds. It tells nothing about its contents.

It's probably a script, instructions for which were already given.

---

### Post by albinootje on 2009-01-10
> **snova said:**
> Linux doesn't use file extensions to denote file type; at the least, it doesn't depend on them.

More than likely, the .linux extension is used simply to tell it apart from the Mac and Windows builds. It tells nothing about its contents.

It's probably a script, instructions for which were already given.

Right.
And if the OP still cannot find the installation instructions, then you can actually try to find out what kind of file type it is about, for example :
```

$ file test1.sh
test1.sh: Bourne-Again shell script text executable

```
Although that doesn't always work so well ;-)
```

$ file Desktop/raidrec.c
Desktop/raidrec.c: ASCII Pascal program text

```

---

