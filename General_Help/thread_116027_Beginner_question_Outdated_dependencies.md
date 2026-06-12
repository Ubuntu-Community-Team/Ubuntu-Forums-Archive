---
title: "Beginner question: Outdated dependencies"
date: 2006-01-11
forum: General Help
---

### Post by marinosr on 2006-01-11
I'm trying to install a software package that is dependent on packages that are outdated. Can I make symbolic links to the new packages? How do I go about doing this? 

Also... how do I use find? The manpage was very difficult to understand. I try find *libid3*, but that doesn't do anything.

---

### Post by timfrost on 2006-01-11
You can't pretend that the older package is installed with symlinks.  There are compatibility packages for some things (eg libc5 vs libc6).  With more specific details about the package you want to install, we may be able to suggest the right solution.  (Note: if the package was built for debian, rather than ubuntu, it may not be possible to satisfy the dependencies correctly.


find needs a path to search, and needs to be told that the name is '*libid3*'.
try
```

 find / -name '*libid3*' -print

```

The '-print' says to print the path name of the file.

---

### Post by marinosr on 2006-01-12
Aha. Thanks for the help on find.

I'm trying to install alba, a tool for unwrapping MP3 files bundled with Album Wrap for Windows. Below is a copy of my terminal session:

> marinosr@RichardMarinos:~/Desktop$ sudo dpkg -i albaextractor_0.4-dev-1_i386.deb
Password:
Selecting previously deselected package albaextractor.
(Reading database ...
66519 files and directories currently installed.)
Unpacking albaextractor (from albaextractor_0.4-dev-1_i386.deb) ...
dpkg: dependency problems prevent configuration of albaextractor:
 albaextractor depends on libid3-3.8.3; however:
  Package libid3-3.8.3 is not installed.
 albaextractor depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Package libwxgtk2.4 is not installed.
dpkg: error processing albaextractor (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 albaextractor


I have libid3-3.8.3c2 and libwxgtk2.4-1 installed on my system. I'm not even sure that my packages are necessarily incompatible, just differently named. What do y'all think?

---

