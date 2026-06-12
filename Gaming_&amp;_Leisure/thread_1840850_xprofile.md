---
title: "xprofile"
date: 2011-09-08
forum: Gaming &amp; Leisure
---

### Post by Sworddragon on 2011-09-08
I searched for an application that is available to load special driver configurations on different applications (like nHancer or the NVIDIA driver on Windows). I couldn't find such an application and even nvidia-settings can just set global values.

I'm programming for some years but most of it was web based. So I enhanced my C knowledge and have written my own application that is available to load a special driver configuration if an application is active. I named it xprofile (because it is a profile manager for X11).

It is available on Sourceforge: [https://sourceforge.net/projects/xprofile/files](https://sourceforge.net/projects/xprofile/files)
There is the source, a binary package and a deb package (I developed the application on oneiric and used the dependencies of it).

It is the first release and there are much things to do. For example I have only a NVIDIA graphic card and can support only these cards (which doesn't mean there will be no ATI support in the future).


**_Example configuration_**

Create the file /etc/xprofile/applications/warcraft_3.conf and write in it:

```
[Warcraft III]
DIGITAL_VIBRANCE=1023

```

After you restart xprofile the colors will be enhanced if Warcraft 3 is active. If you minimize the game the color will be reset. If you restore it the colors will be enhanced again. You get a documentation with man xprofile (or look into the documentation in the source). Digital vibrance is a good example because it should work on the fly on every application. If you want to test it on another application just change the first line to [window_name_of_application] and restart xprofile.

---

### Post by Sworddragon on 2011-09-25
Version 0.1.0 is released. The key changes are:

> - Added support for multiple X-Server
- Optimized performance
- Using regular expressions for the window name
- Added some more graphic options

At next I will make a look to support options like overclocking, underclocking and fan controlling and control them on every single gpu.

---

