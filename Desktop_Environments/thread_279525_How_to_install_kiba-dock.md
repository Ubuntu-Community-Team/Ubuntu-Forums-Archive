---
title: "How to install kiba-dock?"
date: 2006-10-18
forum: Desktop Environments
---

### Post by nyxynyx on 2006-10-18
Hello, im new to linux and i cant seem to install kiba-dock! i did the cvs step, then when i do ./autogen.sh i get lots of errors:

autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
configure.in: 8: required file `./[config.h].in' not found
akamaru/Makefile.am:7: variable `GTK_LIBS' not defined
akamaru/Makefile.am:7: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GTK_LIBS' not defined
dock/Makefile.am:12: variable `GCONF_LIBS' not defined
dock/Makefile.am:12: variable `PANGO_LIBS' not defined
dock/Makefile.am:12: variable `SVG_LIBS' not defined
dock/Makefile.am:12: variable `CAIRO_LIBS' not defined
dock/Makefile.am:12: variable `GLITZ_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GTK_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GCONF_LIBS' not defined
gset-kiba/Makefile.am:8: variable `GLADE_LIBS' not defined
files/Makefile.am:9: variable `glade_DATA' not defined
autoreconf: automake failed with exit status: 1

did i do anything wrong? i followed the instructions:

sudo aptitude install build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev
sudo aptitude install autoconf automake1.9
cvs -d:pserver:anonymous@metascape.afraid.org:/cvsroot co kiba-dock
cd kiba-dock/
./autogen.sh
make
make install-schemas
./utils/populate-dock.sh

thanks!

---

### Post by wieman01 on 2006-10-18
Have you tried following this?

[http://http://ubuntuforums.org/showthread.php?t=268645]("http://http://ubuntuforums.org/showthread.php?t=268645")

---

### Post by dannymichel on 2007-06-12
That thread is out-dated.
The links don't work

---

