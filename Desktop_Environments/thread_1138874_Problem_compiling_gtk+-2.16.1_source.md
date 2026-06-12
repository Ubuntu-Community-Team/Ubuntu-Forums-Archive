---
title: "Problem compiling gtk+-2.16.1 source"
date: 2009-04-26
forum: Desktop Environments
---

### Post by ilikeroflcopters on 2009-04-26
Hi all, sorry if i make any mistakes or leave information out

I just upgraded from Ubuntu 8.10 to 9.04 and when selecting one of the new themes, the Appearance Preferences window showed an error saying i did not have the murrine gtk+ engine installed.I downloaded the source for murrine and when doing "sh ./configure" it told me 
```
checking for GTK... no
configure: error: GTK+-2.10 is required to compile murrine
```
I downloaded the source for gtk+-2.16.1 along with the sources for atk-1.25.2,cairo-1.8.0,pango-1.24.1,glib-2.20.1. I extracted and compiled atk-1.25.2,cairo-1.8.0,pango-1.24.1,glib-2.20.1 with no problems. But when i went to do "sh ./configure" in the gtk+-2.16.1 folder, it told me at the end
```
checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... yes
checking for jpeg_simple_progression in -ljpeg... yes
checking for libpng12... yes
checking for jas_init in -ljasper... no
configure: error:
*** Checks for JPEG2000 loader failed. You can build without it by passing
*** --without-libjasper to configure

```

I downloaded the JPEG image loading library from the link given in the INSTALL file with gtk+-2.16.1.I compiled the library with no problems, but when I go to do "sh ./configure" in the gtk+ folder, it still tells me it cannot find the JPEG image loading library, just like the code above. Does anyone know a possible reason for the JPEG library still being not found?Any help is appreciated greatly :D

---

### Post by snova on 2009-04-26
> **ilikeroflcopters said:**
> I just upgraded from Ubuntu 8.10 to 9.04 and when selecting one of the new themes, the Appearance Preferences window showed an error saying i did not have the murrine gtk+ engine installed.I downloaded the source ...

It's a lot simpler to install the **gtk2-engines-murrine** package from Synaptic.

---

### Post by ilikeroflcopters on 2009-04-26
> **snova said:**
> It's a lot simpler to install the **gtk2-engines-murrine** package from Synaptic.

Yes, it is easier and simpler to just use Synaptic to install murrine, but I want to learn how to compile it from source code.
I want to know why I keep getting an error with gtk+ and the JPEG image loading library not being reckognized, since I have already installed the library.

---

### Post by snova on 2009-04-26
> **ilikeroflcopters said:**
> Yes, it is easier and simpler to just use Synaptic to install murrine, but I want to learn how to compile it from source code.
I want to know why I keep getting an error with gtk+ and the JPEG image loading library not being reckognized, since I have already installed the library.

If you insist. Even if it is worth learning though, it's much more preferable to install it from the package manager so it integrates a bit better... but nothing worth being concerned about.

> **ilikeroflcopters said:**
> ```
checking for GTK... no
configure: error: GTK+-2.10 is required to compile murrine
```

Install the **libgtk2.0-dev** package.

> I downloaded the source for gtk+-2.16.1 along with the sources for atk-1.25.2,cairo-1.8.0,pango-1.24.1,glib-2.20.1. I extracted and compiled atk-1.25.2,cairo-1.8.0,pango-1.24.1,glib-2.20.1 with no problems.

I hope you didn't install over top of system libraries... when it says those libraries are missing, what it's referring to are the -dev packages, which it needs to comple.

> But when i went to do "sh ./configure" in the gtk+-2.16.1 folder, it told me at the end
```
checking for jpeg_destroy_decompress in -ljpeg... yes
checking for jpeglib.h... yes
checking for jpeg_simple_progression in -ljpeg... yes
checking for libpng12... yes
checking for jas_init in -ljasper... no
configure: error:
*** Checks for JPEG2000 loader failed. You can build without it by passing
*** --without-libjasper to configure

```

Probably **libjpeg-dev**.

> I downloaded the JPEG image loading library from the link given in the INSTALL file with gtk+-2.16.1.I compiled the library with no problems, but when I go to do "sh ./configure" in the gtk+ folder, it still tells me it cannot find the JPEG image loading library, just like the code above. Does anyone know a possible reason for the JPEG library still being not found?Any help is appreciated greatly :D

You're going to rebuild half your system at this rate. :P

---

