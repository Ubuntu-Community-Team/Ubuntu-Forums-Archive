---
title: "Kiba-dock black bar problem"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by ryanfx on 2007-08-03
Hey guys - 

I had the kiba-dock running perfectly for about a couple hours and then all of a sudden the program crashed, and now whenever I restart it, it comes up as the typical black bar.  I tried searching for ways to fix this, but none of them seemed applicable to me.

I installed kiba using the method on the Wiki page, (apt-get)



Any ideas?  What info would you like from me to further diagnose this?

I have tried completely removing with (apt-get --purge) and reinstalling, but it just comes up as the black bar still.

I have Beryl installed and working perfectly.

Currently on Feisty Fawn, running an ATI 9800 AIW Pro


```

ryan@ryan-desktop:~$ kiba-dock --verbose
Info Message (main.c @ line 146):
        Kiba was build with SVG support

Info Message (main.c @ line 154):
        Kiba was build without SDL support

Info Message (main.c @ line 160):
        Kiba was build without GLITZ support

Misc Message (main.c @ line 179):
        Initiall RSVG Library

Misc Message (kiba.c @ line 967):
        Initiall Akamaru Engine

Misc Message (kiba.c @ line 799):
        Creating the Window..

Misc Message (main.c @ line 196):
        Loading Plugins...

Misc Message (main.c @ line 76):
        Try to load Plugins from/usr/lib/kiba-dock

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libdbus.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libwinlist.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libclipman.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/liblauncher.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libclock.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libtrash.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libsysinfo.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libvolume.so

Misc Message (plugin.c @ line 747):
        Found Library at /usr/lib/kiba-dock/libtaskbar.so

Misc Message (main.c @ line 201):
        Plugins loaded


Misc Message (render.c @ line 1373):
        Shape Input

```

---

### Post by ryanfx on 2007-08-04
bump

---

