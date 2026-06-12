---
title: "Problems with scilab and tcl/tk"
date: 2006-10-02
forum: Education &amp; Science
---

### Post by BirkBum on 2006-10-02
I am trying to install scilab 4.0 on dapper and I am running into trouble compiling the source. I run into the following problem after running './configure':

[INDENT]...
checking for finite... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking for main in -lncurses... no
checking for main in -lcurses... no
checking for main in -ltermcap... no
checking for main in -ltermlib... no
checking for PVM architecture... LINUX
checking for main in -ldl... yes
checking for header file tcl.h... configure: error: no header file tcl.h  found for 8.4*[/INDENT]

I am new at this so the only thing I could think to do was to install the tcl and tk packages. When I did this I got the following messages:

[INDENT]*sudo apt-get install tcl8.4*
Reading package lists... Done
Building dependency tree... Done
tcl8.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/INDENT]

[INDENT]*sudo apt-get install tk8.4*
Reading package lists... Done
Building dependency tree... Done
tk8.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.[/INDENT]

I interpreted these to mean that tcl/tk is already installed and is the most recent version. Any ideas on what I need to do?

---

### Post by dwight on 2006-10-03
You probably need to install tcl and tk development packages - tcl8.4-dev  and tk8.4-dev .

---

### Post by kleeman on 2006-10-03
I went through this as well and there are a number of other dev packages you need to install as well (you need to decipher the configure messages to work out which). It does work in the end though on Dapper. If you have a 64 bit system pick up my checkinstall deb here

[http://www.yourfilelink.com/get.php?fid=184208](http://www.yourfilelink.com/get.php?fid=184208)

---

### Post by bomanizer on 2007-03-31
Any news on this?

---

### Post by WW on 2007-03-31
Why not install the Linux binary version of 4.1 that is available on the scilab web page?  (Or is that only 32 bit, and you want 64 bit?)

---

