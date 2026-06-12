---
title: "fuppes wont compile"
date: 2007-09-24
forum: Gaming &amp; Leisure
---

### Post by superai2000 on 2007-09-24
checking for libpcre >= 5.0... no
configure: error: Library requirements (libpcre >= 5.0) not met; consider
adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a
nonstandard prefix so pkg-config can find them.

i have the libpcre3 package installed
am i missing something?

---

### Post by DoktorSeven on 2007-09-24
When you're compiling something, you always need the **-dev** version of the needed library package installed.  Search for libpcre3-dev or similar and install.

---

### Post by superai2000 on 2007-09-24
got it

thanks

---

### Post by dave-bloody-colvin on 2010-10-25
The package you need is "Perl 5 Compatibility Regular Expression Library - Development files".

Go to the software centre and type in LIBPcre and it is the bottom of the list.

Then you will need "A C++ interface to the Gnome XML library" 

Then SQL

[http://www.sqlite.org/download.html](http://www.sqlite.org/download.html)

Extract, sodu bash and configure;make;make install

then you need to play with the config file. But it works well once you get used to it.

---

