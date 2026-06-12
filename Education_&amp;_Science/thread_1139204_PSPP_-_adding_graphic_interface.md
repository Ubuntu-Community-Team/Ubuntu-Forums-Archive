---
title: "PSPP - adding graphic interface"
date: 2009-04-26
forum: Education &amp; Science
---

### Post by satimis on 2009-04-26
Hi folks,


PSPP
Debian 5.0, minimal installation
No X running


To add graphic interface do I need installing X?


(see)
The following packages are required to enable PSPP's graphing features.
......
[http://cvs.savannah.gnu.org/viewvc/pspp/INSTALL?revision=1.16&root=pspp&view=markup&pathrev=MAIN](http://cvs.savannah.gnu.org/viewvc/pspp/INSTALL?revision=1.16&root=pspp&view=markup&pathrev=MAIN)


libplot
pkg-config
GTK+
libglade


# apt-cache search libplot```

libplot-dev - The GNU plotutils libraries (development files)
libplot-perl - perl interface to plot library
libplot2c2 - The GNU plotutils libraries
libploticus0 - script driven business graphics library
libploticus0-dev - Development files for the ploticus library
plotutils - The GNU plotutils (plotting utilities) package

```

Which of them shall I install?


# apt-cache policy pkg-config```

pkg-config:
  Installed: (none)
  Candidate: 0.22-1
  Version table:
     0.22-1 0
        500 http://ftp.us.debian.org lenny/main Packages

```

It is available on repo.


# apt-cache search GTK+ | grep gtk+```

bitstormlite - BitTorrent Client based on c++/gtk+2.0
denemo - A gtk+ frontend to GNU Lilypond
gcx - astronomical image processing and photometry gtk+ application
gtk2-engines-murrine - cairo-based gtk+-2.0 theme engine
libdianewcanvas2 - a gtk+2 vectorial canvas with extra features
libdianewcanvas2-dev - a gtk+2 vectorial canvas with extra features
libgdk-pixbuf2 - The GdkPixBuf image library, gtk+ 1.2 version
libglrr-gtk0 - Utility functions for gtk+ of Grift
libglrr-widgets0 - Miscellaneous gtk+ widgets for Grift

```


# apt-cache search GTK+ | grep GTK+

found many of them.  Difficult listing all here.


# apt-cache search libglade```

cairo-clock - An analog clock drawn with vector-graphics
gazpacho - GTK+ User Interface Designer
glade - GTK+ 2 User Interface Builder
glade-gnome - GTK+ 2 User Interface Builder (with GNOME 2 support)
libglade-cni - Java bindings for Glade (native code)
libglade-java - Java bindings for Glade
libglade-java-dev - Java bindings for Glade (development files)
libglade-java-doc - Java bindings for Glade (API documentation)
libglade-java-gcj - Java bindings for Glade (native code for use with
gij)
libglade-jni - Java bindings for Glade (native library)
libglade2-0 - library to load .glade files at runtime
libglade2-dev - development files for libglade
libglade2-ruby - Libglade 2 bindings for the Ruby language
libglade2-ruby1.8 - Libglade 2 bindings for the Ruby language
libglade2.0-cil - CLI binding for the Glade libraries 2.6
libglademm-2.4-1c2a - C++ wrappers for libglade2 (shared library)
libglademm-2.4-dbg - C++ wrappers for libglade2 (debug symbols)
libglademm-2.4-dev - C++ wrappers for libglade2 (development files)
libglademm-2.4-doc - C++ wrappers for libglade2 (documentation)
libgladeui-1-7 - GTK+ User Interface Build core library
libgladeui-1-dev - GTK+ User Interface Build core library (development
files)
libgnomeada2-dbg - Debugging symbols for libgnomeada2
libgnomeada2-dev - Development files for libgnomeada2
libgtk2-gladexml-perl - Perl interface to use user interfaces created
with glade-2
libgtkada2-dbg - Debugging symbols for libgtkada2
libgtkada2-dev - Development files for libgtkada2
libgtkada2-doc - Documentation for libgtkada2
liblua5.1-gtk-0 - gtk bindings for the lua language version 5.1
vim-syntax-gtk - Syntax files to highlight GTK+ keywords in vim
```


Which of them shall I install?  Thanks



Optional:-
libncurses
libreadline
libhistory
texinfo


# apt-cache search libncurses```

centerim-utf8 - A text-mode multi-protocol instant messenger client
libncurses-gst - Ncurses bindings for GNU Smalltalk
libncurses-ruby - ruby Extension for the ncurses C library
libncurses-ruby1.8 - ruby Extension for the ncurses C library
libncurses-ruby1.9 - ruby Extension for the ncurses C library
libncurses5 - shared libraries for terminal handling
libncurses5-dbg - debugging/profiling libraries for ncurses
libncurses5-dev - developer's libraries and docs for ncurses
libncursesw5 - shared libraries for terminal handling (wide character
support)
libncursesw5-dbg - debugging/profiling libraries for ncurses
libncursesw5-dev - developer's libraries for ncursesw

```


Which of them shall I install?


# apt-cache search libreadline```

libreadline-java - GNU readline and BSD editline wrappers for Java
libreadline-java-doc - API docs for readline/editline wrappers for Java
libreadline-ruby - Readline interface for Ruby
libreadline-ruby1.8 - Readline interface for Ruby 1.8
libreadline-ruby1.9 - Readline interface for Ruby 1.9
libreadline5 - GNU readline and history libraries, run-time libraries
libreadline5-dbg - GNU readline and history libraries, debugging
libraries
libreadline5-dev - GNU readline and history libraries, development
files
ruby1.8 - Interpreter of object-oriented scripting language Ruby 1.8
```


Which of them shall I install?


# apt-cache search libhistory
No printout


# apt-cache policy texinfo```
   
texinfo:
  Installed: (none)
  Candidate: 4.11.dfsg.1-4
  Version table:
     4.11.dfsg.1-4 0
        500 http://ftp.us.debian.org lenny/main Packages

```


I'll install it.


Please advise.  TIA


B.R.
satimis

---

### Post by mali2297 on 2009-04-27
> **satimis said:**
> 
To add graphic interface do I need installing X?


Yes.

> 
The following packages are required to enable PSPP's graphing features.
......
[http://cvs.savannah.gnu.org/viewvc/pspp/INSTALL?revision=1.16&root=pspp&view=markup&pathrev=MAIN](http://cvs.savannah.gnu.org/viewvc/pspp/INSTALL?revision=1.16&root=pspp&view=markup&pathrev=MAIN)


libplot
pkg-config
GTK+
libglade

...

Which of them shall I install?

First, install the package build-essential. It will give you the essential build tools to compile from source.

Then install libplot-dev, libgtk2.0-dev, libglade2-dev, libncurses5-dev, libreadline5-dev... Do you see the pattern?

---

### Post by neoflight on 2009-04-27
how about [ncurses]("http://en.wikipedia.org/wiki/Ncurses")?

---

### Post by satimis on 2009-04-28
Hi folks,


Thanks for your advice.


To my surprise after installing xserver-xorg-core and xorg PSPP GUI can be started by running "psppire" on terminal with following table displayed;
```

Untitled0 -- PSPP Data Edition (on vzd4.satimis.com)

```

I don't need to install those packages.  I have no idea what they are used for as described on the manual.


B.R.
satimis

---

### Post by mali2297 on 2009-04-28
> **satimis said:**
> Hi folks,


Thanks for your advice.


To my surprise after installing xserver-xorg-core and xorg PSPP GUI can be started by running "psppire" on terminal with following table displayed;
```

Untitled0 -- PSPP Data Edition (on vzd4.satimis.com)

```

I don't need to install those packages.  I have no idea what they are used for as described on the manual.


B.R.
satimis

Did you really compile from source or did you find a binary package?

---

### Post by satimis on 2009-04-28
> **mali2297 said:**
> Did you really compile from source or did you find a binary package?
Hi Martin,


I installed PSPP from the package on Debian repo, not from source.


B.R.
satimis

---

### Post by mali2297 on 2009-04-29
> **satimis said:**
> Hi Martin,


I installed PSPP from the package on Debian repo, not from source.


B.R.
satimis

GTK+ et cetera are on the list of dependencies for pspp (from [here]("http://packages.debian.org/lenny/pspp")), so you probably have them installed already. Note that the development packages (those ending with -dev) are only needed for building from source.

---

### Post by satimis on 2009-04-29
> **mali2297 said:**
> GTK+ et cetera are on the list of dependencies for pspp (from [here]("http://packages.debian.org/lenny/pspp")), so you probably have them installed already. Note that the development packages (those ending with -dev) are only needed for building from source.
Hi mali2297,

Noted and thanks

satimis

---

