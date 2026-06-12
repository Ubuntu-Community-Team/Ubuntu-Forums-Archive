---
title: "Installing Gimp 2.3.11 Problems with dependancies"
date: 2006-08-13
forum: Desktop Environments
---

### Post by khaledaboualfa on 2006-08-13
I'm trying to install the latest unstable version of gimp (we'll it's been unstable for over a year now but apartenly it's gotten much better in the latest released version). I've downloaded the .deb file from here:

[http://ftp.debian.org/debian/pool/main/](http://ftp.debian.org/debian/pool/main/)

But the problem is after I've run it says:

> Error: Dependancies not saticfiable : gimp|libgimp2.0

Debugging symbols for The GIMP
This package includes the debugging symbols useful for debugging The GIMP and its libraries, contained in the gimp and libgimp2.0 packages. The debugging symbols are used for execution tracing and core dump analysis. 

Now I've got 2.211 installed, do I need to uninstall this first?

---

### Post by kaffelars on 2006-08-13
It seems that you need a newer libgimp as well.
I'm not sure if you need to uninstall Gimp 2.2.11, but it's not unlikely that these two together will cause problems.

I have the Ubuntu default (2.2.11) and then compiled 2.3.10 myself. I installed 2.3.10 in the /opt-directory, so the two versions do not conflict.

It's not hard to compile it yourself if you follow the instructions [here]("http://gimp.org/release-notes/gimp-2.3.html"). To install to  /opt (so you don't get conflicts) remember to type **./configure --prefix=/opt/gimp-2.3** 

Good luck :)

---

