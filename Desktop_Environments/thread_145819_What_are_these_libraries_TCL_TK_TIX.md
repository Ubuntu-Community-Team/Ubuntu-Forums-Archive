---
title: "What are these libraries?? TCL? TK??? TIX???"
date: 2006-03-17
forum: Desktop Environments
---

### Post by Sunnz on 2006-03-17
Hello there,

I am doing a computer system course at school and they have this CPU simulator program... they have the source code for Linux and I like to compile and install on to my system, but I am running into problems.

It seems that this simulator requires these libraries: tcl, tk and tix.

I have tried to install them and tcl-dev and tix-dev and tk-dev... but it still doesn't work!!!

So what's going on? What's the deal with these libraries??? Do I have them installed or not???

I have looked at the messages from make install, it just complaints that it can't find tk.h, tcl.h, nor tix.h.

So what am I suppose to do???

Thanks.

---

### Post by claes on 2006-03-17
Perhaps the program looks for the libraries in the wrong place. Is there a configure script you can run to tell the makefile where the headers are?

Claes

---

### Post by Sunnz on 2006-03-17
The config file asked for the following:```
# SYSTEM CONFIGURATION FOR Tcl/Tk/Tix

# Edit the following paths to reflect the actual locations
# of your TCL, Tk, Tix, and X11 libraries and headers.

TCL_LIB = /usr/lib
TK_LIB = /usr/lib
TIX_LIB = /usr/lib
X11_LIB = /usr/X11R6/lib

TCL_INCLUDE = /usr/include
TK_INCLUDE  = /usr/include
TIX_INCLUDE = /usr/include
X11_INCLUDE = /usr/X11R6/include

# We need to know what your libraries are actually called. Set
# the following constants to the base names of the TCL, Tk, and
# Tix libraries. The base name is the part of the library name
# between `lib' and `.so' or `.a'. The libraries will be found
# in the *_LIB directories you have given above.

TCL_LINK = tcl
TK_LINK = tk
TIX_LINK = tix8.1.8.4


# OTHER LIBS: anything outside of X11, Tcl, Tk and Tix  that the wish needs

# Linux:
OTHER_LIBS = -lm -ldl -lieee

# Solaris 2.4:
#OTHER_LIBS = -lsocket -lnsl -lm -ldl
```

Don't see where is asked for header files at all...

---

### Post by Sunnz on 2006-03-17
Ohh tk.h and tcl.h is actually in /usr/include/tcl8.4/ so it doesn't complaint about that anymore.

But now it complaints that /usr/bin/ld: cannot find -ltk...

What is -ltk? Is it a file????

---

### Post by claes on 2006-03-18
-ltk is that it wants to l=link to tk=tk.h 

So I guess that the makefile can't find tk.h either. Have you change the TK_INCLUDE so it says the same as TCL_INCLUDE?

Claes

---

### Post by Sunnz on 2006-03-20
I think so:

```
# SYSTEM CONFIGURATION FOR Tcl/Tk/Tix

# Edit the following paths to reflect the actual locations
# of your TCL, Tk, Tix, and X11 libraries and headers.

TCL_LIB = /usr/lib
TK_LIB = /usr/lib
TIX_LIB = /usr/lib
X11_LIB = /usr/X11R6/lib

TCL_INCLUDE = /usr/include/tcl8.4
TK_INCLUDE  = /usr/include/tcl8.4
TIX_INCLUDE = /usr/include
X11_INCLUDE = /usr/X11R6/include

# We need to know what your libraries are actually called. Set
# the following constants to the base names of the TCL, Tk, and
# Tix libraries. The base name is the part of the library name
# between `lib' and `.so' or `.a'. The libraries will be found
# in the *_LIB directories you have given above.

TCL_LINK = tcl
TK_LINK = tk
TIX_LINK = tix8.1.8.4


# OTHER LIBS: anything outside of X11, Tcl, Tk and Tix  that the wish needs

# Linux:
OTHER_LIBS = -lm -ldl -lieee
```

---

### Post by Sunnz on 2006-04-09
So... any ideas??

---

