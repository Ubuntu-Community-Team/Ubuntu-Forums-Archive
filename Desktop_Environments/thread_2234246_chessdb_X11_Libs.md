---
title: "chessdb X11 Libs"
date: 2014-07-13
forum: Desktop Environments
---

### Post by Al_Ko on 2014-07-13
Hi Everybody, I have been trying to compile Chessdb (an improvement of SCID) from scratch on my Ubuntu 12.04 LTS machine. When I run ./configure to start compilation process, I get the following message:
```
configure: Makefile configuration program for ChessDB    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.4
    Your operating system is: Linux 3.8.0-39-generic
    Location of "tcl.h": /usr/include/tcl8.4
    Location of "tk.h": /usr/include/tcl8.4
    Location of Tcl 8.4 library: /usr/lib
    Location of Tk 8.4 library: /usr/lib
    Location of X11 library: not found
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile ChessDB.
```

I have tried to edit the makefile and find the library, but all to no avail. I would greatly appreciate it if someone could help or at least tell me what is going on

Thanks!

---

### Post by steeldriver on 2014-07-13
I have no experience with the particular software you are trying to build, so I don't know *which* "X11 library" it is looking for in this case; however if you don't mind the possibility of a few unneeded packages getting installed along the way then installing the xorg-dev metapackage will probably fix it

```

sudo apt-get install xorg-dev

```

From [FONT=courier new]apt-cache show xorg-dev[/FONT]:
```

Description-en: X.Org X Window System development libraries
 This metapackage provides the development libraries for the X.Org X Window
 System.
 .
 X Window System design documentation, manual pages, library reference
 works, static versions of the shared libraries, and C header files are
 supplied by the packages depended on by this metapackage.

```

---

