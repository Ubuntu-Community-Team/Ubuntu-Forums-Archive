---
title: "Problem upgrading Banshee to 0.10.8"
date: 2006-03-23
forum: Desktop Environments
---

### Post by Morbett on 2006-03-23
I'm want to install Banshee 0.10.8, or the latest version. I updated to 0.10.4 through synaptic. When I try to configure Banshee 0.10.8 before running the make file, I get this error:


> checking for MUSICBRAINZ... configure: error: Package requirements (libmusicbrainz >= 2.1.1) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the MUSICBRAINZ_CFLAGS and MUSICBRAINZ_LIBS environment variables
to avoid the need to call pkg-config. See the pkg-config man page for
more details.

Any idea how do I fix this?

---

### Post by o_fortuna on 2006-03-23
[QUOTE=Morbett]I'm want to install Banshee 0.10.8, or the latest version. I updated to 0.10.4 through synaptic. When I try to configure Banshee 0.10.8 before running the make file, I get this error:




Any idea how do I fix this?[/QUOTE]
Install libmusicbrainz4-dev. That should take care of your problem. If not, go into synaptic, search for "libmusicbrainz" (name only) and just install everything. That's what I do if I can't configure something. ;)

---

### Post by Morbett on 2006-03-24
Thanks.  So I was finally able to conig Banshee 0.10.8.  This is what the configuration summarized at the end:

> banshee-0.10.8

    Install Prefix:    /usr
    C Compiler:        gcc
    Mono C# Compiler:  /usr/lib/pkgconfig/../../bin/mcs
    Mono Runtime:      /usr/lib/pkgconfig/../../bin/mono

    Engines:
      GStreamer:       yes, 0.8
      Helix Remote:    no
      VLC:             no

    Digital Audio Players (DAP):
      iPod:            no
      NJB:             yes

    Xing MP3 Encoder:  no
    GStreamer Plugins: /usr/lib/gstreamer-0.8
    DAAP Support:      yes, Avahi





Now when I run the make file, I get these errors:

> ./daap-sharp/Server.cs(525,54): error CS0246: The type or namespace name `Client StateArgs' could not be found. Are you missing a using directive or an assembly reference?
./daap-sharp/Server.cs(568,58): error CS0246: The type or namespace name `EntryG roupStateArgs' could not be found. Are you missing a using directive or an assem bly reference?
./daap-sharp/ServiceLocator.cs(205,48): error CS0246: The type or namespace name  `ServiceInfoArgs' could not be found. Are you missing a using directive or an a ssembly reference?
./daap-sharp/ServiceLocator.cs(215,51): error CS0246: The type or namespace name  `ServiceInfoArgs' could not be found. Are you missing a using directive or an a ssembly reference?
./daap-sharp/ServiceLocator.cs(261,50): error CS0246: The type or namespace name  `ServiceInfoArgs' could not be found. Are you missing a using directive or an a ssembly reference?
Compilation failed: 5 error(s), 0 warnings
make[4]: *** [Daap.dll] Error 1
make[4]: Leaving directory `/home/aidan/banshee-0.10.8/src/Banshee.Plugins/Daap'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/aidan/banshee-0.10.8/src/Banshee.Plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aidan/banshee-0.10.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aidan/banshee-0.10.8'
make: *** [all] Error 2


This one tough program to install...   ](*,)

---

