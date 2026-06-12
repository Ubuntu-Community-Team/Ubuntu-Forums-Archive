---
title: "Problems when installing Enlightenment with the easy_e17 script"
date: 2006-01-09
forum: General Help
---

### Post by hellfire_bg on 2006-01-09
I tried to install Enlightenment with the the easy_e17 script ([http://omicron.homeip.net/projects/easy_e17/easy_e17.sh)](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh)). Everything goes well (cvs checkout, downloading the files etc) until it starts to compile evas. Then i get the following error message:

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /home/hellfire/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Running aclocal...
aclocal: configure.in: 118: macro `AM_PATH_GTK' not found in library
Running aclocal...
aclocal: configure.in: 118: macro `AM_PATH_GTK' not found in library
-----------------------------------------------------------------------------
You surely must have noticed the "previous installed" - this is because i tried this two times. Any ideas?

---

### Post by patrick295767 on 2006-04-20
Me too !!
  
I got such message :
```

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
-----------------------------------------------------------------------------


```
  
solved: with : 

apt-get update


apt-get -f -y install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev


apt-get -f -y install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev 

apt-get -f -y install libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev 

apt-get -f -y install libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev

apt-get -f -y install  autoconf pkg-config libpng3-dev 




apt-get -f -y remove automake1.4 automake1.6 automake1.8 automake1.9
apt-get -f -y install automake1.7
./easy_e17.sh -i --skip=eclair,emotion

---

