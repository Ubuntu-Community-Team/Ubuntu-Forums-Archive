---
title: "Problem to compile plugin for amsn..."
date: 2004-12-18
forum: Desktop Environments
---

### Post by Neo40 on 2004-12-18
Hi, 

I have installed amsn, and now I want to compile plugin for traydock. So, I want to directory ~/amn/plugins/traydock and when I type ./configure I get this error:

eric@ubuntu:~/amsn-0_94/plugins/traydock $ ./configure
checking for Tcl configuration... configure: WARNING: Can't find Tcl configuration definitions

What packages to I need to install to fix this? I have already tcl8.4-dev installed.

Thanks

---

### Post by elmosgot on 2005-04-11
You have to install tcl-8.*-dev tk-8.*-dev and imlib1-dev

# apt-get install tcl-8.4-dev tk-8.4-dev imlib1-dev

Try this:

# cd msn/utils/linux/traydock
# ./configure --with-tk=/usr/lib/tk8.4/ --with-tcl=/usr/lib/tcl8.4/
# make

---

