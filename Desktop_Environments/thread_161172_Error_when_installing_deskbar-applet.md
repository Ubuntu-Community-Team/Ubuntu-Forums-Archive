---
title: "Error when installing deskbar-applet"
date: 2006-04-16
forum: Desktop Environments
---

### Post by ernando on 2006-04-16
Dear all,
When I try to install deskbar-applet on my breezy I got this error :

user@Marketing:~/Downloads/deskbar-applet-2.13.90$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Someone can help me ? Thanks...

---

### Post by Ramses de Norre on 2006-04-16
sudo apt-get install build-essential

---

### Post by ernando on 2006-04-16
Thanks for your solution, I still have this error :

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

Could you help me ?
Thanks

---

### Post by Ramses de Norre on 2006-04-16
sudo apt-get install libxml-xerces-perl

---

### Post by ernando on 2006-04-16
Many thanks, I tried but still get this error :

checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

Any idea ?

---

