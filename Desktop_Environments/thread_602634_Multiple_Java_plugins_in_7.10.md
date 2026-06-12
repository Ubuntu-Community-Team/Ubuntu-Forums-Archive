---
title: "Multiple Java plugins in 7.10"
date: 2007-11-04
forum: Desktop Environments
---

### Post by lofftjm on 2007-11-04
Hi,

I'm ugin Ubuntu 7.10, Firefox 2.0.0.8.  I need to use multiple version of the Java plugin.  I've downloade the three version I need and unpacked them into the following locations:

/usr/lib/jvm/jdk1.5.0_09
/usr/lib/jvm/jdk1.5.0_11
/usr/lib/jvm/jdk1.5.0_12

I then created the following symbolic links:

sudo ln -s /usr/lib/jvm/jdk1.5.0_09/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/jpi1.5.0_09

sudo ln -s /usr/lib/jvm/jdk1.5.0_11/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/jpi1.5.0_11

sudo ln -s /usr/lib/jvm/jdk1.5.0_12/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/jpi1.5.0_12

When I start Firefox and go to "about:plugins" I nly see Java(TM) Plug-in 1.5.0_12-b04 and Java(TM) Plug-in 1.5.0_11-b03 regisstered.  Is there any log file I can check to see why the 1.5.0_09 plugin is not resistered?

---

### Post by pismikrop on 2007-11-04
you may see the error output via using:
$ firefox
from terminal.

---

### Post by lofftjm on 2007-11-04
I started it from the command line, but didn't see anything relevant....

---

### Post by lofftjm on 2007-11-07
Anyone have any ideas on this?

---

