---
title: "Configure error"
date: 2009-05-19
forum: General Help
---

### Post by GabrielWolff on 2009-05-19
I try to configure a Gimp plugin, and get this error message upon trying to compile:
```
gabriel@gabriel-laptop:~/Desktop/focusblur-3.2.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether to enable maintainer-specific portions of Makefiles... no
checking for native Win32... no
checking for an ANSI C-conforming const... yes
checking for gdk-pixbuf-csource... no
configure: error: Could not find gdk-pixbuf-csource in your PATH
gabriel@gabriel-laptop:~/Desktop/focusblur-3.2.4$ make

```
Help?

---

### Post by Bindsa on 2009-05-19
```
 
configure: error: Could not find gdk-pixbuf-csource in your PATH

```
 
Thats the problem, it looks like the directory you're running the commands from should have gdk-pixbuf-csource in it. Try redownloading the plugin, from another link if possible, then try to reinstall. Hope that fixes it.

---

### Post by GabrielWolff on 2009-05-19
> **Bindsa said:**
> ```
 
configure: error: Could not find gdk-pixbuf-csource in your PATH

```
 
Thats the problem, it looks like the directory you're running the commands from should have gdk-pixbuf-csource in it. Try redownloading the plugin, from another link if possible, then try to reinstall. Hope that fixes it.

Great, I got around that.
But then make goes right and make install gives me this:
```
gabriel@gabriel-laptop:~/Desktop/focusblur-3.2.4$ make install
Making install in po
make[1]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/po'
/bin/sh .././mkinstalldirs /usr/share
/usr/bin/install: cannot create regular file `/usr/share/locale/it/LC_MESSAGES/gimp20-focusblur.mo': Permission denied
installing it.gmo as /usr/share/locale/it/LC_MESSAGES/gimp20-focusblur.mo
/usr/bin/install: cannot create regular file `/usr/share/locale/ja/LC_MESSAGES/gimp20-focusblur.mo': Permission denied
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/gimp20-focusblur.mo
/usr/bin/install: cannot create regular file `/usr/share/locale/ru/LC_MESSAGES/gimp20-focusblur.mo': Permission denied
installing ru.gmo as /usr/share/locale/ru/LC_MESSAGES/gimp20-focusblur.mo
if test "focusblur" = "gettext-tools"; then \
	  /bin/sh .././mkinstalldirs /usr/share/gettext/po; \
	  for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /usr/share/gettext/po/$file; \
	  done; \
	  for file in Makevars; do \
	    rm -f /usr/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
make[1]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/po'
Making install in pixmaps
make[1]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
make  install-am
make[2]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
make[3]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
make[2]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
make[1]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/pixmaps'
Making install in src
make[1]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/src'
make[2]: Entering directory `/home/gabriel/Desktop/focusblur-3.2.4/src'
test -z "/usr/lib/gimp/2.0/plug-ins" || mkdir -p -- "/usr/lib/gimp/2.0/plug-ins"
  /usr/bin/install -c 'focusblur' '/usr/lib/gimp/2.0/plug-ins/focusblur'
/usr/bin/install: cannot create regular file `/usr/lib/gimp/2.0/plug-ins/focusblur': Permission denied
make[2]: *** [install-libexecPROGRAMS] Error 1
make[2]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/gabriel/Desktop/focusblur-3.2.4/src'
make: *** [install-recursive] Error 1
gabriel@gabriel-laptop:~/Desktop/focusblur-3.2.4$ 

```
What's Error 1 and what's Error 2?

---

### Post by oldos2er on 2009-05-19
You need to run "sudo make install" so that you have write permission in /usr/lib/gimp/2.0/plug-ins/focusblur .

---

### Post by GabrielWolff on 2009-05-19
> **oldos2er said:**
> You need to run "sudo make install" so that you have write permission in /usr/lib/gimp/2.0/plug-ins/focusblur .

Duuuh!

Thanks, worked perfectly.

I can erase the downloaded folder now, right?

---

### Post by oldos2er on 2009-05-19
If you ever want to uninstall the program, you'll need to keep the source folder. Otherwise you can delete it.

---

### Post by nulldev on 2009-06-26
> **GabrielWolff said:**
> Great, I got around that.

How did you got around that? I'm still stuck. :confused:

---

### Post by DigitalWolf333 on 2009-07-28
me too O_o

---

### Post by typhoon476 on 2009-09-12
You need to install libgtk2.0-dev to get gdk-pixbuf-csource executable.
Just do:

$ sudo aptitude install libgtk2.0-dev

And you'll be fine.


Cheers,

---

