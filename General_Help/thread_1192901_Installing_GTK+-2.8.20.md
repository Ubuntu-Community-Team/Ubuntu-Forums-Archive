---
title: "Installing GTK+-2.8.20"
date: 2009-06-20
forum: General Help
---

### Post by akrchstn on 2009-06-20
Okay I'm going to try to go as in depth as possible to get help figuring this out.

I found out how to install rezlooks using this ```
./configure --prefix=/usr
```But it said I needed gtk 2.8 so I went to go get gtk 2.8. Went into terminal and put ```
cd gtk+-2.8.20
./configure
``` and it spit out this ```
No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```So I went to get the packages I need "glib", "atk", "pango", and "cairo"
First I tried installing the glib package. Went to terminal, put ```
cd glib-2.21.0
./configure
```and it said this
```
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. (http://www.gnu.org/software/gettext/gettext.html
```So I went and got gettext and did my ```
cd gettext 
./configure
make
make install
``` and it worked fine then I went and tried glib again and it came out with the same error. I decided to go try the cairo package next so I download it, go to terminal type ```
cd cairo-1.2.4
./configure
```and I get ```
checking for cairo's Microsoft Windows font backend... 
checking whether cairo's Microsoft Windows font backend could be enabled... no (requires a Win32 platform)
checking for cairo's PNG backend... 
configure: WARNING: Could not find libpng in the pkg-config search path
checking whether cairo's PNG backend could be enabled... no
configure: error: requested PNG backend could not be enabled
```I have no idea what that means so I hope somebody can enlighten me. Then I move on to the pango package I needed, so I download it, go to terminal put in ```
cd pango-1.12.3
./configure
and it spits this out [code]checking for CAIRO... configure: error: *** Didn't find any of FreeType, X11, ATSUI or Win32.
*** Must have at least one backend to build Pango.
```By reading that I understand that I need Cairo installed but that doesn't work.
Next I try the atk package, go to terminal, type ```
cd atk-1.11.4
./configure 
```And I get this ```
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```
Can somebody please help. It seems like I'm just going in circles

---

### Post by akrchstn on 2009-06-20
Bump for help

---

### Post by michy99 on 2009-06-20
There's really no reason to compile rezlooks from source code. Just download the .deb file and double-click on it to install.

[http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)

---

### Post by akrchstn on 2009-06-20
> **michy99 said:**
> There's really no reason to compile rezlooks from source code. Just download the .deb file and double-click on it to install.

[http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)

This happens ```
Selecting previously deselected package rezlooks-0.6.
(Reading database ... 135768 files and directories currently installed.)
Unpacking rezlooks-0.6 (from .../rezlooks-0.6_0.6-1_i386.deb) ...
dpkg: error processing /home/alex/rezlooks-0.6_0.6-1_i386.deb (--install):
 trying to overwrite ' /usr/lib/gtk-2.0/2.4.0/engines/librezlooks.la', which is also in package rezlooks-0.4
Errors were encountered while processing:
 /home/alex/rezlooks-0.6_0.6-1_i386.deb
```

---

### Post by akrchstn on 2009-06-21
Umm, bump

---

### Post by artshark on 2009-07-22
> **akrchstn said:**
> Umm, bump
need help with the same get gettext error!

---

### Post by cmost on 2009-07-22
Since Ubuntu releases are frozen in time at the point of their release, installing newer packages (i.e., GTK 2.8.xx) will be problematic because they will invariably require libraries that are not up to date.  This is the case with GTK 2.8.xx.  Your options are to use a DEB compiled by someone else, track down the myriad dependencies and other required files, or wait for the next Ubuntu release which will likely have the updated package.  Or switch to a rolling distribution (like Debian Testing, Gentoo, Arch, PCLinuxOS) that updates core packages regularly.

---

### Post by dannymichel on 2010-04-26
> **cmost said:**
> Since Ubuntu releases are frozen in time at the point of their release, installing newer packages (i.e., GTK 2.8.xx) will be problematic because they will invariably require libraries that are not up to date.  This is the case with GTK 2.8.xx.  Your options are to use a DEB compiled by someone else, track down the myriad dependencies and other required files, or wait for the next Ubuntu release which will likely have the updated package.  Or switch to a rolling distribution (like Debian Testing, Gentoo, Arch, PCLinuxOS) that updates core packages regularly.

anybody find an x64 .deb?

---

### Post by dannymichel on 2010-05-04
> **michy99 said:**
> There's really no reason to compile rezlooks from source code. Just download the .deb file and double-click on it to install.

[http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb](http://rapidshare.com/files/15311808/rezlooks-0.6_0.6-1_i386.deb)there is no x64 deb

---

### Post by morteza1991 on 2011-06-24
I installed glib-2.28.8 when i want install pango-1.28.4 see ```
configure: error:
*** Glib 2.24.0 or better is required. The latest version of
*** Glib is always available from ftp://ftp.gtk.org/.
```

---

