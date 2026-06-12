---
title: "Dell XPS13 Citrix ICA / npviewer.bin"
date: 2013-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tubesenf on 2013-05-27
Greetings,

on my XPS 13 with Ubuntu 12.04 LTS i have a problem getting Citrix ICA up and running.
I followed the instructions on help.ubuntu.com and so on but i think i have a different problem.

When i try to execute /usr/lib/nspluginwrapper/i386/linux/npviewer.bin i get a permission denied.

file mode is 755.

Any idears??

Thanks 

Daniel

---

### Post by tubesenf on 2013-05-27
Some more details:

 nspluginwrapper -v -i /opt/Citrix/ICAClient/npica.so 
linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: Permission denied
linux32: /usr/lib/nspluginwrapper/i386/linux/npviewer.bin: Permission denied
nspluginwrapper: no appropriate viewer found for /opt/Citrix/ICAClient/npica.so


dpkg -l |grep nsplu
ii  nspluginviewer:i386                    1.4.4-0ubuntu4                          A wrapper to run Netscape plugins on other architectures
ii  nspluginwrapper                        1.4.4-0ubuntu4                          A wrapper to run Netscape plugins on other architectures
obi@wp4711:~/Downloads$ dpkg -l |grep citrix
obi@wp4711:~/Downloads$ dpkg -l |grep -i citrix
ii  icaclient:i386                         12.1.0                                  Citrix Receiver for Linux

dpkg -l |grep -i flashplu
ii  flashplugin-installer                  11.2.202.285ubuntu0.12.04.1             Adobe Flash Player plugin installer
obi@wp4711:~/Downloads$ dpkg -l |grep -i motif4
ii  libmotif4                              2.3.3-5ubuntu1.12.04.1                  Open Motif - shared libraries
ii  libmotif4:i386                         2.3.3-5ubuntu1.12.04.1                  Open Motif - shared libraries

---

