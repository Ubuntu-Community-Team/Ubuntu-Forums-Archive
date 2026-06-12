---
title: "gnome alarm applet"
date: 2005-08-06
forum: Desktop Environments
---

### Post by anando on 2005-08-06
I am looking for a Ubuntu package for gnome alarm applet [[http://home.freeuk.net/igbarn/alarm-applet.html]](http://home.freeuk.net/igbarn/alarm-applet.html]). Any pointers will be gratefully acknowledged.

I tried compiling the code available in the above website. The problem is that in the Makefile, they have things like 
PREFIX = `gnome-config --prefix applets`

Presumably we are calling the command gnome-config with arguments to figure out the default applet prefix directory - however I could not find gnome-config command in my Ubuntu 5.04 - I even installed gnome-devel (which in turn installed a bunch of other packages) - but still no gnome-config.

Any suggestions ? 

Thanks,
Anando.

---

### Post by Sam on 2005-08-06
Why don't you download a RPM package and convert it to DEB with 'alien' ?

---

### Post by anando on 2005-08-06
[QUOTE=Sam]Why don't you download a RPM package and convert it to DEB with 'alien' ?[/QUOTE]

I tried that as well ... there are dependency problems ... 

Here is what I did 

sengupta >> sudo alien alarm-applet-0.8.9-1.i586.rpm
Password:
alarm-applet_0.8.9-2_i386.deb generated

sengupta >> sudo dpkg -i alarm-applet_0.8.9-2_i386.deb 
Selecting previously deselected package alarm-applet.
(Reading database ... 118781 files and directories currently installed.)
Unpacking alarm-applet (from alarm-applet_0.8.9-2_i386.deb) ...
Setting up alarm-applet (0.8.9-2) ...


However when I tried to run it, I got the following error
alarm_applet: error while loading shared libraries: libpanel_applet.so.1: cannot open shared object file: No such file or directory

When I ldd'd the executable I found that there are more dynamic lib 'not found' problems :

sengupta >> ldd /usr/bin/alarm_applet
                 libesd.so.0 => /usr/lib/libesd.so.0 (0x4e5de000)
        libaudiofile.so.0 => /usr/lib/libaudiofile.so.0 (0x4e5ea000)
        libpanel_applet.so.1 => not found
        libgnorba.so.27 => /usr/lib/libgnorba.so.27 (0x43a6c000)
        libORBitCosNaming.so.0 => /usr/lib/libORBitCosNaming.so.0 (0x4406f000)
        libORBit.so.0 => /usr/lib/libORBit.so.0 (0x44031000)
        libIIOP.so.0 => /usr/lib/libIIOP.so.0 (0x44079000)
        libORBitutil.so.0 => /usr/lib/libORBitutil.so.0 (0x4402d000)
        libgnomeui.so.32 => /usr/lib/libgnomeui.so.32 (0x4398b000)
        libart_lgpl.so.2 => /usr/lib/libart_lgpl.so.2 (0x43f16000)
        libgdk_imlib.so.1 => /usr/lib/libgdk_imlib.so.1 (0x44008000)
        libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0x4db37000)
        libICE.so.6 => /usr/X11R6/lib/libICE.so.6 (0x4db1d000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0x4ea8b000)
        libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0x4e8c4000)
        libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0x4e827000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0x4dafb000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0x4da34000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x4da0c000)
        libgnome.so.32 => /usr/lib/libgnome.so.32 (0x43970000)
        libgnomesupport.so.0 => /usr/lib/libgnomesupport.so.0 (0x43969000)
        libdb.so.3 => not found
        libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0x4e8fc000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x4da2f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x4d8dd000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x4e532000)
        libpopt.so.0 => /lib/libpopt.so.0 (0x4e333000)
        libz.so.1 => /usr/lib/libz.so.1 (0x43956000)
        libwrap.so.0 => /lib/libwrap.so.0 (0x44083000)
        libdb3.so.3 => /usr/lib/libdb3.so.3 (0x4db54000)
        libXi.so.6 => /usr/X11R6/lib/libXi.so.6 (0x4e14f000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x4d8c5000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x4db42000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0x4dd62000)

Any ideas ?

Thanks
Anando.

---

