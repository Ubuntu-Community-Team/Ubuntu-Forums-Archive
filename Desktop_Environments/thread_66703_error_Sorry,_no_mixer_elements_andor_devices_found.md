---
title: "error: Sorry, no mixer elements and/or devices found"
date: 2005-09-18
forum: Desktop Environments
---

### Post by mabuti on 2005-09-18
Hello, I could use some help here. I have just installed Ubuntu Warthog on my Dell Inspriron 510m notebook.
There is no sound at all.
When I click on volume control, I get the following message:Sorry, no mixer elements and/or devices found.
I hope the following will be useful to you in understanding my problem:

user@ubuntu:~ $ lsof /dev/dsp
lsof: status error on /dev/dsp: No such file or directory
lsof 4.71
 latest revision: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/)
 latest FAQ: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ)
 latest man page: [ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man](ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man)
 usage: [-?abhlnNoOPRstUvV] [+|-c c] [+|-d s] [+D D] [+|-f]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+|-M] [-o [o]] [-p s]
 [+|-r [t]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Use the ``-h'' option to get more help information.
user@ubuntu:~ $

mabuti@ubuntu:~ $ lsof /dev/snd/*
mabuti@ubuntu:~ $

Please help

---

