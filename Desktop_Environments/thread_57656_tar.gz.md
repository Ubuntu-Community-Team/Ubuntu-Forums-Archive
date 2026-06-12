---
title: "tar.gz ?"
date: 2005-08-17
forum: Desktop Environments
---

### Post by aks123 on 2005-08-17
Sorry for this noob question...but what is a tar.gz file, and how do I install a program with a "tar.gz" extension?

---

### Post by mtelewicz on 2005-08-17
"tar.gz" is really a tar archive that has been gzipped.  You can uncompress it using the tar utility, like so:

tar xzvf file.tar.gz

Or you can use gunzip to "ungzip" it then use the tar utility:

gunzip file.tar.gz
tar xvf file.tar

Hope this helps!

---

### Post by mtelewicz on 2005-08-17
I should also mention this other thing, even though you haven't directly asked about it.  You may run into something similar with the extension "tar.bz2".  This is a tar archive that has been compressed with bzip2.  You can uncompress and expand the archive using the tar utility by doing:

tar xjvf filename.tar.bz2

Notice the difference in the options for tar.  z = gzip, j = bzip2.

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=aks123]Sorry for this noob question...but what is a tar.gz file, and how do I install a program with a "tar.gz" extension?[/QUOTE]

It is usually the program source code.  There are lots of threads on the forum how to build and install software from source-- look for keywords "checkinstall" and "build-essentials".  Generally, it can try your patience before you resolve all the dependencies.  It is usually easier to ask if someone knows where you can get a .deb of the program or see if someone knows a repostiory it is in.

---

