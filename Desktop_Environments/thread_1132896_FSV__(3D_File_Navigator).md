---
title: "FSV  (3D File Navigator)?"
date: 2009-04-22
forum: Desktop Environments
---

### Post by suffer1989 on 2009-04-22
Anyone remember Jurassic park ? Remember that cool unix file browser ?

anyways, there appears the be a program :

[http://fsv.sourceforge.net/](http://fsv.sourceforge.net/)

that simulates the effect. Basically, its a 3d file navigator. 

Anyways: here is th download page :

[http://sourceforge.net/project/showfiles.php?group_id=31220](http://sourceforge.net/project/showfiles.php?group_id=31220)

Im wondering if it will run on ubuntu 8.10. I cant install it yself, as im a recent PC convert, and the only thing i do know how to instal is by using DEB files...

:confused:

Sooo, if it does work, how does one go about installing, and running it ?

---

### Post by celticbhoy on 2009-04-22
Have a look here for some other 3D interfaces :-

[http://nooface.net/3dui.shtml](http://nooface.net/3dui.shtml)

---

### Post by oldos2er on 2009-04-22
> **suffer1989 said:**
> Anyone remember Jurassic park ? Remember that cool unix file browser ?

anyways, there appears the be a program :

[http://fsv.sourceforge.net/](http://fsv.sourceforge.net/)

that simulates the effect. Basically, its a 3d file navigator. 

Anyways: here is th download page :

[http://sourceforge.net/project/showfiles.php?group_id=31220](http://sourceforge.net/project/showfiles.php?group_id=31220)

Im wondering if it will run on ubuntu 8.10. I cant install it yself, as im a recent PC convert, and the only thing i do know how to instal is by using DEB files...

:confused:

Sooo, if it does work, how does one go about installing, and running it ?

 This is very old. I tried compiling it, but it requires an older version of gtk.

---

### Post by celticbhoy on 2009-04-22
Its not the same thing, but if you want something different, have a look at eagle mode file manager:-

[http://eaglemode.sourceforge.net/](http://eaglemode.sourceforge.net/)

---

### Post by zhocchao on 2009-04-22
you can install fsv in intrepid and it works. It's not worth the trouble (not somuch trouble though). Eaglemode is better.

---

### Post by Runaway1956 on 2009-12-30
> **oldos2er said:**
> This is very old. I tried compiling it, but it requires an older version of gtk.

I've attempted to compile the older GTK packages - but they depend on Pango, and I can't even figure out which Pango packages I need.  

So far, I've probably spent 4 hours on exploring dependencies, and I'm about to give up, unless I stumble over an easy how-to.  ;)

---

### Post by intense.feel on 2010-08-05
Yeeeah,the latest version of FSV it's fully working on Lucid Lynx :D
after installing these:
libgtk1.2-common_1.2.10-18.1_all.deb
libgtk1.2_1.2.10-18.1_i386.deb
libgtk1.2-dev_1.2.10-18.1_i386.deb
libglib1.2ldbl_1.2.10-19_i386.deb
libglib1.2-dev_1.2.10-19_i386.deb
gtkglarea5_1.2.3-3_i386.deb
gtkglarea5-dev_1.2.3-3_i386.deb
;)

---

### Post by DIFTOW on 2010-09-12
> **intense.feel said:**
> Yeeeah,the latest version of FSV it's fully working on Lucid Lynx :D
after installing these:
libgtk1.2-common_1.2.10-18.1_all.deb
libgtk1.2_1.2.10-18.1_i386.deb
libgtk1.2-dev_1.2.10-18.1_i386.deb
libglib1.2ldbl_1.2.10-19_i386.deb
libglib1.2-dev_1.2.10-19_i386.deb
gtkglarea5_1.2.3-3_i386.deb
gtkglarea5-dev_1.2.3-3_i386.deb
;)

When I type sudo apt-get install in the terminal, i get this.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package libgtk1.2-common_1.2.10-18.1_all.deb**


I'm also running 64 bit, so I'm assuming those files with "i386" are not gonna run for me.

---

### Post by intense.feel on 2010-09-16
> **DIFTOW said:**
> When I type sudo apt-get install in the terminal, i get this.


I'm also running 64 bit, so I'm assuming those files with "i386" are not gonna run for me.

Don't use apt-get. Download these packages from internet (I used some debian site but i don't remmember URL  [I think it was [http://www.debian.org/distrib/packages]](http://www.debian.org/distrib/packages]) but i can upload them if you want [i386]) and install with dpkg -i. I don't know if is this working on 64bit systems but i think it can if you will install libraries for 64 architecture.

---

### Post by HuckBerry on 2011-03-12
I hate to bump a year old thread. But I've been fighting FSV for hours now. I had managed to find each of the files you mentioned prior to finding this thread, however my ./configure still errs out on "gtkglarea". Here's some info:
```

$ dpkg -l | grep libgtk1.2
ii  libgtk1.2                            1.2.10-18.1build2ak2                       The GIMP Toolkit set of widgets for X
ii  libgtk1.2-common                     1.2.10-18.1build2ak2                       Common files for the GTK+ library
ii  libgtk1.2-dbg                        1.2.10-18.1build2ak2                       Debugging files for the GIMP Toolkit
ii  libgtk1.2-dev                        1.2.10-18.1build2ak2                       Development files for the GIMP Toolkit
ii  libgtk1.2-doc                        1.2.10-18.1build2ak2                       Documentation for the GIMP Toolkit

$ dpkg -l | grep libglib
ii  libglib-perl                         1:1.221-1                                  Perl interface to the GLib and GObject libra
ii  libglib1.2-dev                       1.2.10-19build1ak2                         The GLib library of C routines (development)
ii  libglib1.2ldbl                       1.2.10-19build1ak2                         The GLib library of C routines
ii  libglib2.0-0                         2.22.3-0ubuntu1                            The GLib library of C routines
ii  libglib2.0-cil                       2.12.9-1                                   CLI binding for the GLib utility library 2.1
ii  libglib2.0-data                      2.22.2-0ubuntu1                            Common files for GLib library
ii  libglib2.0-dev                       2.22.3-0ubuntu1                            Development files for the GLib library
ii  libglibmm-2.4-1c2a                   2.22.1-2                                   C++ wrapper for the GLib toolkit (shared lib

$ dpkg -l | grep gtkgl
ii  gtkglarea5                           1.2.3-3                                    Gimp Toolkit OpenGL area widget shared libra
ii  gtkglarea5-dev                       1.2.3-3                                    Gimp Toolkit OpenGL area widget include file
ii  libgtkgl2.0-1                        2.0.0-1                                    OpenGL area for GTK (shared libraries)
ii  libgtkgl2.0-dev                      2.0.0-1                                    OpenGL area for GTK (development files)
ii  libgtkglarea0.0-cil                  0.0.17-4                                   CLI bindings for the GTK OpenGL area widget


```

the error I'm getting is:

```

checking for GTK - version >= 1.2.1... yes
checking for glBegin in -lMesaGL... no
checking for glBegin in -lGL... yes
checking for gtk_gl_area_new in -lgtkgl... no
configure: error: Cannot find gtkglarea

```

I'm 99% sure I have the right version of gtkglarea but just in case I was wondering if you had maybe one more package you forgot to mention.

EDIT:// 
I'm on Karmic (9.10) btw, I just reread the op and noticed it said lynx.

---

### Post by NickD-NLUG on 2011-09-23
I'm stuck in the same place, on natty.... any ideas?

---

