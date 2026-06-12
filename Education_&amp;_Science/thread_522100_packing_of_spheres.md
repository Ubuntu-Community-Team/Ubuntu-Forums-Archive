---
title: "packing of spheres"
date: 2007-08-10
forum: Education &amp; Science
---

### Post by in_flu_ence on 2007-08-10
Is there any software that can calculate the maximum packing of spheres?

E.g. FCC packing => 0.74 assuming sphere of equal size.

I have spheres of difference sizes (say, two size groups). I want to have a software that account for the maximum packing. Any chance?

Thanks.

---

### Post by renzokuken on 2007-08-10
chemistry is it?

i don't any off hand but it shouldnt be too hard to write a small script to calculate it for you

---

### Post by in_flu_ence on 2007-08-10
yah it is mainly chemistry.

Not only do i want to calculate that, i really would also like to visualise it. so that I can know exactly the interaction of the spheres.

nonetheless, i will try to do some simple calculation on paper.

---

### Post by euler_fan on 2007-08-11
[GAMGI]("http://www.gnomefiles.org/app.php?soft_id=401")

Is this what you are looking for?

There are algorithms to do random close packing which may be the only way to get the job done since at least superficially your problem seems to resemble the knapsack problem. Not sure how badly you want to write a software implementation of any of them yourself since there are plenty of sticking points, especially in numerical algorithms.

---

### Post by renzokuken on 2007-08-12
wow thats an awesome link euler 

i might find that useful too

---

### Post by in_flu_ence on 2007-08-13
any chance that someone has a short explanation on how to install this? WHat packages are needed?

Thanks. Looks good so wanna try out.

---

### Post by euler_fan on 2007-08-13
It looked like source only . . . you can try searching for the name of the program in Synaptic to see if there is a version already packaged for Ubuntu.

If source, then there are plenty of tutorials on the forums about installing from source.

---

### Post by in_flu_ence on 2007-08-13
Yah it seems to be source only and not in synaptic. I might have thought some member have tried it and see if i have the luck to get a summaried installation guide:P

I am also not very sure which pacakges (required ones) that I have to pre-install before I install gamgi.

:)

---

### Post by euler_fan on 2007-08-13
After unpacking the source to a folder in your /home directory, run 

```
./configure
```

That should tell you what you're missing.

You won't be able to successfully configure until you have all the required files. (At least that's what I remember the last time I had that issue).

Then run ```
make
``` and [CODE] sudo made install [\CODE]

If that doesn't work, please post.

---

### Post by renzokuken on 2007-08-14
there is a list of dependencies for gamgi on their homepage [www.gamgi.org](www.gamgi.org) and most of them should be in the repos.

i'll reboot into ubuntu later this avo and have a go at installing it then let you know how it went

---

### Post by in_flu_ence on 2007-08-14
Would be appreciated Renzokuken. Actually, I am just lazy and don't really have much time these days for trial and error. Otherwise, I shouldn't have posted such post here:P

In any case, hope a success for you and guide me through the EASY way:P

---

### Post by renzokuken on 2007-08-15
i've tried a few things but i'm not getting very far, keeps spitting out the following after running **make**

```
robn@zanpakto:~/GAMGI/gamgi0.12.8/src$ make
gcc -g -Wall -ansi -c -I./engine -I./gtk/gamgi -I./gtk/window -I./gtk/layer -I./gtk/light -I./gtk/assembly -I./gtk/cell -I./gtk/cluster -I./gtk/molecule -I./gtk/group -I./gtk/plane -I./gtk/direction -I./gtk/atom -I./gtk/bond -I./gtk/text -I./gtk/help -I./gtk -I./mesa -I./math -I./chem -I./phys -I./io -I./expat -I./global -I/usr/include/freetype2 -I/usr/include -I/usr/include/gtkgl -I/usr/lib/ -I/usr/lib/ -I/usr/include/GL -I/usr/X11R6/include ./engine/gamgi_engine_array.c -o gamgi_engine_array.o
In file included from ./engine/gamgi_engine_array.c:12:
./engine/gamgi_engine.h:24:22: error: X11/Xlib.h: No such file or directory
./engine/gamgi_engine.h:25:19: error: GL/gl.h: No such file or directory
./engine/gamgi_engine.h:26:20: error: GL/glu.h: No such file or directory
./engine/gamgi_engine.h:27:21: error: gtk/gtk.h: No such file or directory
./engine/gamgi_engine.h:28:29: error: gtkgl/gtkglarea.h: No such file or directory
In file included from ./engine/gamgi_engine_array.c:12:
./engine/gamgi_engine.h:646: error: expected specifier-qualifier-list before &#8216;GtkWidget&#8217;
make: *** [gamgi_engine_array.o] Error 1

```

i thought i had the dependencies met but obviously not. no idea what i'm missing really.

---

### Post by tweedledee on 2007-08-15
> **renzokuken said:**
> i've tried a few things but i'm not getting very far, keeps spitting out the following after running **make**

Do you have the build-essential package installed?  You probably also need libgtk2.0-dev to get most of the remaining missing files.  I'm not actually trying to compile this, but you can quickly check whether the files are installed on your system by ```
find /usr/ -name $NAME
``` (replace $NAME as desired).  For example, I have the X11 development libraries and so have Xlib.h on my system, but not the gtk development libraries (which will install X11 and numerous others), so don't have gtk.h.

If that doesn't work, search the forums here for specific file names to identify which packages they are hiding in.  Alternatively, if you DO have the files installed, you probably have a path problem (either in your system path or in the configure file).

---

### Post by renzokuken on 2007-08-15
yeah i deffo have build-essential, i also installed the other deps (expat, freetype and gtkglarea).

i think the problem actually lies with the paths in the **make_local** file, i tried variations but with no luck

---

### Post by renzokuken on 2007-08-15
heres the make_local
```

##########################################
#
# $GAMGI/src/make_local
#
# Copyright (C) 2004 Carlos Pereira
#
# Distributed under the terms of the GNU
# General Public License: $GAMGI/LICENSE
#

#===============================================================================
#
#                   insert your local library paths 
#                                 or 
#                uncomment usual configurations below
#
#===============================================================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/home/carlos/gamgi/lib/glib/glib/include \
#	-I/home/carlos/gamgi/lib/glib/glib/lib/glib/include
#PATH_GTK_H = -I/home/carlos/gamgi/lib/gtk/gtk/include
#PATH_MESA_H = -I/home/carlos/gamgi/lib/mesa/mesa/include
#PATH_GTKGL_H = -I/home/carlos/gamgi/lib/gtkgl/gtkglarea/include
#PATH_EXPAT_H = -I/home/carlos/gamgi/lib/expat/expat/include
#PATH_FREETYPE_H = -I/home/carlos/gamgi/lib/freetype/freetype/include \
#	-I/home/carlos/gamgi/lib/freetype/freetype/include/freetype
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/home/carlos/gamgi/lib/glib/glib/lib
#PATH_GTK_L = -L/home/carlos/gamgi/lib/gtk/gtk/lib
#PATH_MESA_L = -L/home/carlos/gamgi/lib/mesa/mesa/lib
#PATH_GTKGL_L = -L/home/carlos/gamgi/lib/gtkgl/gtkglarea/lib
#PATH_EXPAT_L = -L/home/carlos/gamgi/lib/expat/expat/lib
#PATH_FREETYPE_L = -L/home/carlos/gamgi/lib/freetype/freetype/lib
#
#===================== Debian Sid/Sarge ================================
 
PATH_X_H = -I/usr/X11R6/include
PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include
PATH_GTK_H = -I/usr/include/gtk-1.2
PATH_MESA_H = -I/usr/include/GL
PATH_GTKGL_H = -I/usr/include/gtkgl
PATH_EXPAT_H = -I/usr/include
PATH_FREETYPE_H = -I/usr/include/freetype2

PATH_X_L = -L/usr/X11R6/lib
PATH_GLIB_L = -L/usr/lib
PATH_GTK_L = -L/usr/lib
PATH_MESA_L = -L/usr/lib
PATH_GTKGL_L = -L/usr/lib
PATH_EXPAT_L = -L/usr/lib
PATH_FREETYPE_L = -L/usr/lib

#========================== x86_64 Linux Suse 10.0 =============================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/opt/gnome/include/glib-1.2 \
#       -I/opt/gnome/lib64/glib/include -I/opt/gnome/include
#PATH_GTK_H = -I/opt/gnome/include/gtk-1.2
#PATH_MESA_H = -I/usr/include
#PATH_GTKGL_H = -I/opt/gnome/include/gtkgl/
#PATH_EXPAT_H = -L/usr/include
#PATH_FREETYPE_H = -I/usr/include/freetype2 \
#       -I/usr/include/freetype2/freetype/config
#
#PATH_X_L = -L/usr/X11R6/lib64
#PATH_GLIB_L = -L/opt/gnome/lib64
#PATH_GTK_L = -L/opt/gnome/lib64
#PATH_MESA_L = -L/usr/lib64
#PATH_GTKGL_L = -L/opt/gnome/lib64
#PATH_EXPAT_L = -I/usr/lib64
#PATH_FREETYPE_L = -L/usr/lib64
#
#========================= PC Linux Red Hat 7.1 ================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include/
#PATH_GTK_H = -I/usr/include/gtk-1.2
#PATH_MESA_H = -I/usr/include/GL
#PATH_GTKGL_H = -I/usr/include/gtkgl
#PATH_EXPAT_H = -I/usr/include/expat
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/usr/lib/glib
#PATH_GTK_L = -L/usr/lib
#PATH_MESA_L = -L/usr/lib
#PATH_GTKGL_L = -L/usr/lib
#PATH_EXPAT_L = -L/usr/lib
#
#===================== Mac Linux Yellow Dog 2.2 ================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include
#PATH_GTK_H = -I/usr/include/gtk-1.2
#PATH_MESA_H = -I/usr/include/
#PATH_GTKGL_H = -I/usr/include/gtkgl
#PATH_EXPAT_H = -I/usr/include
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/usr/lib
#PATH_GTK_L = -L/usr/lib
#PATH_MESA_L = -L/usr/lib
#PATH_GTKGL_L = -L/usr/lib
#PATH_EXPAT_L = -L/usr/lib
#
#===================== PC Linux Suse 8.1 =======================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include/
#PATH_GTK_H = -I/usr/include/gtk-1.2
#PATH_MESA_H = -I/usr/include/GL
#PATH_GTKGL_H = -I/usr/include/gtkgl
#PATH_EXPAT_H = -I/usr/include
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/usr/lib
#PATH_GTK_L = -L/usr/lib
#PATH_MESA_L = -L/usr/lib
#PATH_GTKGL_L = -L/usr/lib
#PATH_EXPAT_L = -L/usr/lib
#
#===================== PC Linux Suse 9.x =======================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/opt/gnome/include/glib-1.2 -I/opt/gnome/lib/glib/include/
#PATH_GTK_H = -I/opt/gnome/include/gtk-1.2
#PATH_MESA_H = -I/usr/include/GL
#PATH_GTKGL_H = -I/opt/gnome/include/
#PATH_EXPAT_H = -I/usr/include/
#PATH_FREETYPE_H = -I/usr/include/ -I/usr/include/freetype2/freetype/
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/opt/gnome/lib
#PATH_GTK_L = -L/opt/gnome/lib
#PATH_MESA_L = -L/usr/lib
#PATH_GTKGL_L = -L/opt/gnome/lib
#PATH_EXPAT_L = -L/usr/lib
#PATH_FREETYPE_L = -L/usr/lib
#
#============================== Mac OS X / Fink ================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/sw/include/glib-1.2 -I/sw/lib/glib/include/
#PATH_GTK_H = -I/sw/include/gtk-1.2
#PATH_MESA_H = -I/usr/X11R6/include
#PATH_GTKGL_H = -I/sw/include/gtkgl
#PATH_EXPAT_H = -I/sw/include
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/sw/lib
#PATH_GTK_L = -L/sw/lib
#PATH_MESA_L = -L/usr/X11R6/lib
#PATH_GTKGL_L = -L/sw/lib
#PATH_EXPAT_L = -L/sw/lib
#
#========================= PC Linux Mandrake 9.2  ================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include/
#PATH_GTK_H = -I/usr/include/gtk-1.2
#PATH_MESA_H = -I/usr/X11R6/include/GL
#PATH_GTKGL_H = -I/usr/include/gtkgl
#PATH_EXPAT_H = -I/usr/include
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/usr/lib
#PATH_GTK_L = -L/usr/lib
#PATH_MESA_L = -L/usr/X11R6/lib
#PATH_GTKGL_L = -L/usr/lib
#PATH_EXPAT_L = -L/usr/lib
#
#===================== Debian 3.0 r1 Woody ================================
#
#PATH_X_H = -I/usr/X11R6/include
#PATH_GLIB_H = -I/usr/include/glib-1.2 -I/usr/lib/glib/include
#PATH_GTK_H = -I/usr/include/gtk-1.2
#PATH_MESA_H = -I/usr/include/GL
#PATH_GTKGL_H = -I/usr/include/gtkgl
#PATH_EXPAT_H = -I/usr/include
#
#PATH_X_L = -L/usr/X11R6/lib
#PATH_GLIB_L = -L/usr/lib
#PATH_GTK_L = -L/usr/lib
#PATH_MESA_L = -L/usr/lib
#PATH_GTKGL_L = -L/usr/lib
#PATH_EXPAT_L = -L/usr/lib
#

```

---

### Post by in_flu_ence on 2007-08-15
Do the path fall exactly like debian? I don't have an answer so i ask:)

I also suspect that it is more likely a path problem in your case from the files that you were missing.

Keep going and I try to find sometime to try it out myself this weekend

Can that be that you are having a 64bit PC and the lib are at the wrong path?

Thanks anyway.

---

### Post by renzokuken on 2007-08-16
the default debian paths dont work.

i'm pretty sure the problem stems from the gtk-1.2 dependency.

ps, its all 32 bit at my end

---

### Post by tweedledee on 2007-08-16
> **renzokuken said:**
> yeah i deffo have build-essential, i also installed the other deps (expat, freetype and gtkglarea).

i think the problem actually lies with the paths in the **make_local** file, i tried variations but with no luck

You should be able to determine the correct paths by using the find command I gave above for the files it says it can't find.  Though the default Debian paths should work...  I spent most of the day yesterday troubleshooting these sorts of problems to get Amber installed on one of our lab machines, so let me know what you find with the file locations versus the paths it is expecting and I may be able to offer a solution.  The problem may be a path, but most ilkely you'll have to fix it in config.h rather than make_local.  Though I've found that research software requiring compiling would benefit immensely if the authors would bother to spend a couple of hours testing it before releasing it...

---

### Post by renzokuken on 2007-08-16
i already tried find but with no luck.

thats why i say a dependancy problem, i dont think i have them installed correctly/at all

---

### Post by tweedledee on 2007-08-16
> **renzokuken said:**
> i already tried find but with no luck.

thats why i say a dependancy problem, i dont think i have them installed correctly/at all

You mean you are in fact missing some of the files?  If you list specific ones you know aren't on your system, I may be able to suggest specific packages that will include them.

Or do you mean they are installed and in the expected location, but the compile still fails?

---

