---
title: "looking for manpages for C standard headers (ex. sys/stat.h)"
date: 2009-02-02
forum: General Help
---

### Post by mdecler2 on 2009-02-02
As the title says, I am looking for the set of manpages from the Ubuntu repository for C standard library headers. 

For example, I need to use the stat() function in my program. I downloaded the POSIX manpages from the Ubuntu repo to learn how to use stat(). The manpage says,
> int stat(const char *restrict path, struct stat *restrict buf);
...
The buf argument is a pointer to a stat structure, as defined in the <sys/stat.h> header, into which information is placed concerning the file.


I can search for the sys/stat.h manpages online, but it would be helpful to have these manpages downloaded so I don't have to go searching online all the time.

---

### Post by jespdj on 2009-02-02
I don't know about man pages, but if you install the package **glibc-doc**, you'll get HTML documentation about the standard C library in /usr/share/doc/glibc-doc.

---

### Post by geirha on 2009-02-02
Install [manpages-dev](apt:manpages-dev). Then ```
man 2 stat
``` should give you the man-page for the stat functions, instead of the stat command.

EDIT: BTW, for programming related questions, you'll usually get a quicker response if you ask in the Programming Talk forum (under the forum category Development & Programming).

---

### Post by knightsamar on 2010-09-23
Thanks a lot! I love ubuntu forums :)

---

