---
title: "Java-applet error - can't find librarys"
date: 2006-04-25
forum: Desktop Environments
---

### Post by Pekz0r on 2006-04-25
I'm trying to run an Java-applet on my apache webserver. But the applet won't load and get the following error:
[http://nwp-gaming.no-ip.org/javaerror.txt](http://nwp-gaming.no-ip.org/javaerror.txt)

The applet is located here:
[http://nwp-gaming.no-ip.org/javaerror.txt](http://nwp-gaming.no-ip.org/javaerror.txt)

I guess i have to install the following packets: libX11.so.6, libXext.so.6, libXtst.so.6, libXp.so.6, libXi.so.6 (and perhaps some more) but i can find them with apt-cache search. 
This is all can find with the command 'apt-cache search libx11' is:
libx11-6 - X11 client-side library
libx11-6-dbg - X11 client-side library (debug package)
libx11-dev - X11 client-side library (development headers)
xlibs-dev - X Window System client library development files transitional package
libx11-freedesktop-desktopentry-perl - perl interface to Freedesktop.org .desktop files
libx11-protocol-perl - Perl module for the X Window System Protocol, version 11

do i have to edit the sources.list? 
or do i need to download and install them? If that's the case, where can i find them?

Thanks

---

### Post by kaamos on 2006-04-25
> I guess i have to install the following packets: libX11.so.6, libXext.so.6, libXtst.so.6, libXp.so.6, libXi.so.6
Those are files, not packages. The packages you need to install the get those files are these
```
sudo apt-get install libx11-6 libxext6 libxtst6 libxp6 libxi6
```
You can use the "Search the contents of packages" in [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/) to search.

---

