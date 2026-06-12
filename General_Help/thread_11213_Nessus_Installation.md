---
title: "Nessus Installation"
date: 2005-01-14
forum: General Help
---

### Post by charlie on 2005-01-14
Just installed a fresh 4.10 and updated all the packages.  Started a "sh nessus-install.sh" installation of Nessus and it stalled a few times asking for Flex, Bison, gcc, and so on.  I installed each of those and then got through nearly the entire installation and the install failed and offered me an install log with a couple hundred lines in it. Looking at the end, there's nothing obvious to me as to why it failed. I have done the same install on RH 7.2 and 9 without any issues. Anyone done a Nessus installlation on Ubuntu?

thanks,
Charlie
[http://geocities.com/jphistoricalsociety/](http://geocities.com/jphistoricalsociety/)

---

### Post by habadaba on 2005-06-24
also trying but it gives the following :

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
The command 'gtk-config' was not found in your $PATH.

---

### Post by odin on 2005-07-14
It may be that I dont understand what you are trying to do but if what you want is install nessus in ubuntu warty,why dont you try with apt-get install nessus or with synaptics?.

I've done it like that and I have nessus running perfectly.

 :)

---

