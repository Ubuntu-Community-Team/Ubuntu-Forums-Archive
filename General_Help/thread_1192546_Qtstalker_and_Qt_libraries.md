---
title: "Qtstalker and Qt libraries"
date: 2009-06-20
forum: General Help
---

### Post by Jefferythewind on 2009-06-20
Hello, 

  I am using Ubuntu 9.04 and I am trying to install a program called Qt stalker.  It is a program for technical analysis of the equity markets.  Anyways i am having a hard time installing it.  I get a lot of error messages during the "make" phase of the installation. (It is a .tar package).  I don't think i have installed the Qt development libraries, which are required.  It says i need Qt 3.3.  Can anyone help me on how to do this?  I have been looking on the Qt website and in the synaptic manager and i don't really know what i am looking for.  

 Thanks for any help!

---

### Post by mlamorey on 2009-08-16
I have installed and uninstalled a couple of times.
It seems pretty straight forward but... maybe not.
I still think there are certain features of the program not working for me with regards to graphing single stock futures.

If you add "deb http://www.zwets.com/qtstalker/"
into your /etc/apt/sources.list then you can just choose it from synaptic.
But following the direction at [http://qtstalker.sourceforge.net/install.html](http://qtstalker.sourceforge.net/install.html)
is probably not a bad idea for all of the pre-conditions. All of the preconditions are available from the synaptic manager. Make sure you get them all. Hard to tell sometimes.

Requirements

    * A Linux or FreeBSD compatible or Mac OS X operating system.
    * Qt development library. At least Qt 3.3.* version. Qt 4 not yet supported.
    * Berkeley DB database. At least db-4.1 version. FreeBSD users are required to use the 4.3 version.
    * TA-Lib Technical Analysis Library. At least ta-lib-0.3.0 version. See below.

---

### Post by Jefferythewind on 2009-09-04
he cool thanks for the reply, i'll try that source

---

