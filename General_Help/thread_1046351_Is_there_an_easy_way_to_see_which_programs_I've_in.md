---
title: "Is there an easy way to see which programs I've installed via svn?"
date: 2009-01-21
forum: General Help
---

### Post by DJ_Peng on 2009-01-21
This may be an odd questions, but I know I've installed a few programs from Subversion and I forgot to make a note of which apps I've gotten that way. Is there any way that I can find a list of which apps came from svn?

---

### Post by sedawk on 2009-01-21
Here is what I would try to find files that have not been installed
using the debian packaging tool (e.g svn, self-compiled sources, 
etc.).

* Have a look at /usr/bin and /usr/local/bin with "ls -rtl *"
  Browsing through the list and have a look at the sorted
  timestamps. This should give you a good idea about the origin
  of the files. Most source packages publish binaries in these
  directories (unless you overwrite that behaviour with
  "./configure --prefix=..." - something I always (try to) do when
  compiling and installing stuff myself).

* Look for (executable) files that are newer than the files from
  your basic installation. E.g. files newer than 90 days:
```
sudo find / -type f -perm /u+x -mtime -90 -print
```
  The problem is that this also lists updates of the last 90 days.

* You can create a list of all officially installed (executable) files
  by running dpkg -l (to get a list of all installed packages) and
  then dpkg -L for every package. You can compare that full list (after
  sorting it with "sort" and removing duplicates with "uniq")
  to a list of all (executable) files on the system
 (created with "find" again, see above).

---

### Post by DJ_Peng on 2009-01-21
Hmmm. I can't do much about it now but I'll check it out tomorrow. Thanks.

---

