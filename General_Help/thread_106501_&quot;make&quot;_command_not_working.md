---
title: "&quot;make&quot; command not working"
date: 2005-12-20
forum: General Help
---

### Post by equal on 2005-12-20
I'm trying to instal a program, snes9express, which is a GUI frontend to snes9x. I've decompressed the source, I run the ./configure command without any problems, but then I try the make command, and here's what comes out

```
$ make
g++ -DHAVE_CONFIG_H -I. -I. -I.  -DS9XDATADIR=\"/usr/local/share/snes9express\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -c frend.cc
frend.cc: In function ‘std::string fr_syserr()’:
frend.cc:3115: error: ‘errno’ was not declared in this scope
make: *** [frend.o] Error 1

```

any clues as to what's going wrong?

---

### Post by Mustard on 2005-12-20
Just for your information, snes9express is available from the multiverse repository and can be installed using synaptic package manager or by using sudo apt-get install snes9express in terminal.

You may need to enable extra repositories to gain access to the multiverse repo.

---

