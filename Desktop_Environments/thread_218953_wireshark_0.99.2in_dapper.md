---
title: "wireshark 0.99.2in dapper"
date: 2006-07-19
forum: Desktop Environments
---

### Post by rextency on 2006-07-19
I'm new to linux and I've been trying to install wireshark witht he gnome interface for 3 days now.  Its been one dependency problem after another.  The end goal is GTK+ 2.10.0 needs to be installed on Dapper.  This has been a huge pain.  One final thing I can't get installed is Cairo.  Cairo requires freetype and freeconfig.  I've installed both, but the Cairo configure script says that they aren't installed.  I installed both in the manner of.
freetype:  ./configure  and also ./configure --prefix=/usr/lib
fontconfig: ./configure  and also ./configure --prefix=/usr/lib

I looked through the Cairo configure script and I can't understand why it can't find these two things.  Anyone have any idea?

---

