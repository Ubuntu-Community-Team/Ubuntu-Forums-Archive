---
title: "Can't Install Nessus Client"
date: 2006-08-18
forum: Desktop Environments
---

### Post by omenix on 2006-08-18
Im triying to install the Nessus Client however, I just got this error 

checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

------

I already installed the libgtk

# dpkg -s libgtk2.0-0
Package: libgtk2.0-0
Status: install ok installed

---

### Post by omenix on 2006-08-18
Just found the solution..

You need the libgtk2.0-dev

sudo apt-get install libgtk2.0-dev

---

