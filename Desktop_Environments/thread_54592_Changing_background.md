---
title: "Changing background"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Owdy on 2005-08-05
[http://www.kde-look.org/content/show.php?content=27384](http://www.kde-look.org/content/show.php?content=27384)

Where do i change that btuuons bacground? I mean that 'start' button in bottom left?

---

### Post by daller on 2005-08-05
Download kbfx:

[http://kde-look.org/content/download.php?content=24898&id=2&PHPSESSID=1d3e9df80144068a5d5e964b9d963bf9](http://kde-look.org/content/download.php?content=24898&id=2&PHPSESSID=1d3e9df80144068a5d5e964b9d963bf9)

Download KuLunch:

[http://www.kde-look.org/content/download.php?content=27384&id=1&PHPSESSID=9ae86749f4796a506307f05293e61720](http://www.kde-look.org/content/download.php?content=27384&id=1&PHPSESSID=9ae86749f4796a506307f05293e61720)

Unpack kbfx and run "sh configure" in the new directory as root...

Run make and make install, and now kbfx is installed!

---

### Post by Owdy on 2005-08-05
[QUOTE=daller]Download kbfx:

[http://kde-look.org/content/download.php?content=24898&id=2&PHPSESSID=1d3e9df80144068a5d5e964b9d963bf9](http://kde-look.org/content/download.php?content=24898&id=2&PHPSESSID=1d3e9df80144068a5d5e964b9d963bf9)

Download KuLunch:

[http://www.kde-look.org/content/download.php?content=27384&id=1&PHPSESSID=9ae86749f4796a506307f05293e61720](http://www.kde-look.org/content/download.php?content=27384&id=1&PHPSESSID=9ae86749f4796a506307f05293e61720)

Unpack kbfx and run "sh configure" in the new directory as root...

Run make and make install, and now kbfx is installed![/QUOTE]
 checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by daller on 2005-08-05
apt-get install gcc

...As far as i recall!

---

### Post by drummer on 2005-08-05
sudo apt-get install build-essential

---

### Post by Owdy on 2005-08-05
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by Owdy on 2005-08-07
Help please. It stops in this: 

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

---

### Post by Owdy on 2005-08-07
Okay, after installing something, got to make part. It gives errors:

bg.xpm:8: warning: deprecated conversion from string constant to `char*'
bg.xpm:8: warning: deprecated conversion from string constant to `char*'
bg.xpm:8: warning: deprecated conversion from string constant to `char*'

What is that?

---

