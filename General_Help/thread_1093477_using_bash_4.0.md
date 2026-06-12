---
title: "using bash 4.0"
date: 2009-03-11
forum: General Help
---

### Post by pytheas22 on 2009-03-11
I wanted to play with bash 4.0, so I downloaded the source from [http://ftp.gnu.org/gnu/bash/](http://ftp.gnu.org/gnu/bash/) and installed it with configure; make; make install (this isn't a production machine so I'm not worried about the potential problems of replacing the bash environment that Ubuntu expects...although so far there are none).  This is a Hardy machine.

I rebooted, and my new bash shell is indeed version 4.0.0, according to 'bash --version'.  But none of the [exciting new features]("http://tiswww.case.edu/php/chet/bash/NEWS") seem to be working.  For example, when I type 'autocd' I just get a 'command not found' message, and the ** 'glob' operator doesn't do anything.

I'm wondering if I'm either not calling these things in the right way, or if I didn't compile bash with support for them enabled.  I don't know how else to call them, though, and the INSTALL file included with the source code says that these features should be included by default.

Does anyone have any pointers?  Probably because bash 4 is so new, there's little documentation for it online that I could find.

---

### Post by vamped on 2009-06-03
> **pytheas22 said:**
> ... none of the exciting new features seem to be working.  For example, when I type 'autocd' I just get a 'command not found' message, and the ** 'glob' operator doesn't do anything.


Those features have to be enabled:

$ shopt -s autocd
$ shopt -s dotglob

To use autocd: just type the name of the directory you want to change into, just like "cd directory" but without the "cd"

To use dotglob, you can for example:
$ ls **/name_of_file
and it will search recursively for the file.

BUT THE REAL SOLUTION IS TO READ THE DOCUMENTATION, which currently is at [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html). There you can search the web page for "autocd" or "**".

---

