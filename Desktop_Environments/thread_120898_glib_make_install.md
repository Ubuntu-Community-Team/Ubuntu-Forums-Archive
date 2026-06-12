---
title: "glib make install"
date: 2006-01-23
forum: Desktop Environments
---

### Post by hellohenry on 2006-01-23
hey can anyone help me - trying to get some programs to run on ubuntu, in particular abc torrent for bittorrent and gtkpod for ipod. 
I can configure and make glib (2.8.0) but when I try make install I receive the following error message

/bin/sh ./mkinstalldirs /usr/local/bin
/usr/bin/install -c glib-gettextsize /usr/local/bin/glib-gettextize
/usr/bin/install: cannot create regular file '/usr/local/bin/glib-gettextize': Permission denied
make [3]: *** [install-binSCRIPTS] Error 1
make [3]: Leaving directory '/home/henry/Desktop/glib-2.8.0'

etc.....

that folder /usr/local/bin is empty, and when I check the user 'permissions' it says I can't write there and I can't change it as I am not the Owner.

can you help? thanks!
henry

---

### Post by RAOF on 2006-01-23
[QUOTE=hellohenry]hey can anyone help me - trying to get some programs to run on ubuntu, in particular abc torrent for bittorrent and gtkpod for ipod. 
I can configure and make glib (2.8.0) but when I try make install I receive the following error message

/bin/sh ./mkinstalldirs /usr/local/bin
/usr/bin/install -c glib-gettextsize /usr/local/bin/glib-gettextize
/usr/bin/install: cannot create regular file '/usr/local/bin/glib-gettextize': Permission denied
make [3]: *** [install-binSCRIPTS] Error 1
make [3]: Leaving directory '/home/henry/Desktop/glib-2.8.0'

etc.....

that folder /usr/local/bin is empty, and when I check the user 'permissions' it says I can't write there and I can't change it as I am not the Owner.

can you help? thanks!
henry[/QUOTE]
Well, you should run "sudo make install" rather than "make install".  The sudo part gives you the root privs you need to modify stuff on the system.

But lets back up a bit.  Why are you compiling glib anyway?  If you manage to successfully install it there's a good chance you'll break all sorts of programs.  You should be able to install gtkpod from synaptic, and ABC is a python program, and as such should just run.  Maybe you'll need to install python, though.

Learn to use Synaptic (GUI, you can find it in System->Administration->Synaptic package manager) and/or apt-get/aptitude (terminal).  They download, install, & set up everything for you, including any dependencies.  Plus, you can easily uninstall programs you've installed with them.

---

### Post by hellohenry on 2006-01-23
thanks
well abctorrent needs wxpython, when I try to configure this happens:

checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:

The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.

so I checked gtk+2.8.0, which will not configure either as this happens:

configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

so I kindof need glib for gtk+   - should I try to do the sudo make install then? or is it dangerous,. or is it possible to make this program work without gtk/glib?
thanks a lot
henry

---

### Post by RAOF on 2006-01-23
Once again, you could try installing wxpython from Synaptic - a quick search in synaptic shows that python-wxgtk2.6 is probably the package you need.  Try installing that.

Synaptic contains (almost) **everything** you'll ever need.  Compiling from source should be the very last resort.  And in the rare times when you **do** need to compile from source, almost all of the dependencies will be in Synaptic.  The packages required for compiling are all marked with <somepackage>-dev names (for example, liblame-dev is the development package for liblame).  

The answer is synaptic, and it's awesome "search" button.

---

### Post by hellohenry on 2006-01-23
thanks very much :0)

---

### Post by BLTicklemonster on 2006-01-23
I'm trying to install stuff, and I keep getting this same message on many of them:

```
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.

```

I have a later version of glib installed, 2.9 I think, so what can I do to make the package use the older version (if I even have it, and if I don't where do I get it)

---

### Post by RAOF on 2006-01-23
[QUOTE=BLTicklemonster]I'm trying to install stuff, and I keep getting this same message on many of them:

```
checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.

```

I have a later version of glib installed, 2.9 I think, so what can I do to make the package use the older version (if I even have it, and if I don't where do I get it)[/QUOTE]
Once again, do you **have** to install from source?  Have you checked Synaptic?  What is it you're trying to install?

If you do have to install from source, check that you've got the libglib2.0-dev package installed - just having the libglib2.0 package installed is not enough, it doesn't contain the development stuff required to compile programs that use it.

---

### Post by BLTicklemonster on 2006-01-23
[QUOTE=RAOF]Once again, do you **have** to install from source?  Have you checked Synaptic?  What is it you're trying to install?

If you do have to install from source, check that you've got the libglib2.0-dev package installed - just having the libglib2.0 package installed is not enough, it doesn't contain the development stuff required to compile programs that use it.[/QUOTE]
Oh, it's been several things, and I can't remember any of them off hand, but they come as tar.gx files, and I try to do what I'm supposed to do, and each time, the nut up right off the bat at ./configure. I suppose they weren't that big a deal if I can't remember them, but it's a real pain to not be able to install something you want. And none of them were in synaptic. No big deal if no one can say "do this" like when you need gcc-3.4 instead of 4.0, there's some voodoo stuff you can do to make it use 3.4 to compile. Thanks anyway.

---

### Post by RAOF on 2006-01-24
[QUOTE=BLTicklemonster]Oh, it's been several things, and I can't remember any of them off hand, but they come as tar.gx files, and I try to do what I'm supposed to do, and each time, the nut up right off the bat at ./configure. I suppose they weren't that big a deal if I can't remember them, but it's a real pain to not be able to install something you want. And none of them were in synaptic. No big deal if no one can say "do this" like when you need gcc-3.4 instead of 4.0, there's some voodoo stuff you can do to make it use 3.4 to compile. Thanks anyway.[/QUOTE]
You **have** got the libglib2.0-dev package installed?  What are the dependencies of the app?  You need to know a lot more about the app in order to compile it from source.

---

### Post by BLTicklemonster on 2006-01-28
Well, can we back up and get rid of the newer ones and go back to that earlier version? If so, how?

---

### Post by RAOF on 2006-01-29
[QUOTE=BLTicklemonster]Well, can we back up and get rid of the newer ones and go back to that earlier version? If so, how?[/QUOTE]
Search in synaptic.  You'll find that there's a libglib1.2-dev package.  That's what you're after.

---

### Post by BLTicklemonster on 2006-01-29
:D libglib? all this time i was looking for glib. Thanks! :cool:

---

### Post by RAOF on 2006-01-29
[QUOTE=BLTicklemonster]:D libglib? all this time i was looking for glib. Thanks! :cool:[/QUOTE]
Synaptic search (or apt-cache search, or aptitude search from the console) is your friend, especially when installing something from source.  I got that package name with "aptitude search glib" from a console - there's about a page of packages matching that, but it's pretty obvious which one you want - it's this line:
```
id  libglib1.2-dev                   - Development files for GLib library         

```

---

### Post by BLTicklemonster on 2006-01-29
Well, my problem is, I have glib 2.8.3 so the files I try to use geek on me wanting just glib 2. Back to square one, how to get around this?

---

### Post by RAOF on 2006-01-29
So, you've installed the libglib1.2-dev package?  Can you include the relevant error message that ./configure produces now?

---

### Post by BLTicklemonster on 2006-01-30
Wow. I'd have to do some real digging to figure out what it was that I was trying to install, though I think I posted the error here abouts somewhere. I'll look and see.

---

### Post by BLTicklemonster on 2006-01-30
See my post here: [http://www.ubuntuforums.org/showthread.php?p=664126#post664126](http://www.ubuntuforums.org/showthread.php?p=664126#post664126)

---

### Post by kaamos on 2006-01-30
uname -r only shows the kernel version. You can check if you have 686 with "uname -m"

---

