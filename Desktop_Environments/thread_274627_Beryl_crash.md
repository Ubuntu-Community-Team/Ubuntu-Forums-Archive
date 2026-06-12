---
title: "Beryl crash"
date: 2006-10-10
forum: Desktop Environments
---

### Post by dckirba on 2006-10-10
Hello all,

I'm not sure if this is where i should post or help regardig Beryl. If not, please point me to the right forum.

I currently don't have a modem at home, so I have to download packages manually elsewhere and install them at home. I had trouble finding all the compiz packages: [http://www.ubuntuforums.org/showthread.php?t=273047](http://www.ubuntuforums.org/showthread.php?t=273047)
so I went ahead with Beryl.

I have an Xgl session set up on my machine. I'm running Dapper.

The first time I ran Beryl-manager, I got the splash and then the screen went all white. I can open a terminal and other apps using alt-F2, but I can't see them. alt-tab shows me what is open, but the windows as such are not visible.

Beryl then filed a crash and defaulted to metacity. Everytime I choose beryl as the window-manager from the manager, screen whites out as above. I can see newly opening windows as lighter spaces in the white, but nothing else.

The output I got in the terminal is:

```
XGL Present
Initiating splash
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/beryl-xgl, process 5183
(no debugging symbols found)
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libXinerama.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /lib/ld-linux.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/beryl/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /usr/lib/beryl/libsettings.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libsettings.so
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/beryl/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libcrashhandler.so
Reading symbols from /usr/lib/beryl/libdecoration.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libdecoration.so
Reading symbols from /usr/lib/beryl/libsplash.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libsplash.so
Reading symbols from /usr/lib/beryl/libwobbly.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libwobbly.so
Reading symbols from /usr/lib/beryl/libanimation.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libanimation.so
Reading symbols from /usr/lib/beryl/libfade.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libfade.so
Reading symbols from /usr/lib/beryl/libcube.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libcube.so
Reading symbols from /usr/lib/libcairo.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/librsvg-2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/librsvg-2.so.2
Reading symbols from /usr/lib/libgdk_pixbuf-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgdk_pixbuf-2.0.so.0
Reading symbols from /usr/lib/libgobject-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libgsf-1.so.113...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgsf-1.so.113
Reading symbols from /usr/lib/libcroco-0.6.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcroco-0.6.so.3
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libexpat.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /lib/libbz2.so.1.0...(no debugging symbols found)...done.
Loaded symbols for /lib/libbz2.so.1.0
Reading symbols from /usr/lib/beryl/librotate.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/librotate.so
Reading symbols from /usr/lib/beryl/libzoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libzoom.so
Reading symbols from /usr/lib/beryl/libscale.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libscale.so
Reading symbols from /usr/lib/beryl/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libmove.so
Reading symbols from /usr/lib/beryl/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libresize.so
Reading symbols from /usr/lib/beryl/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libplace.so
Reading symbols from /usr/lib/beryl/libswitcher.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libswitcher.so
Reading symbols from /usr/lib/beryl/libwater.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libwater.so
Reading symbols from /usr/lib/beryl/libtrailfocus.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libtrailfocus.so
Reading symbols from /usr/lib/beryl/libneg.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libneg.so
Reading symbols from /usr/lib/beryl/libbs.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libbs.so
Reading symbols from /usr/lib/beryl/libput.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libput.so
Reading symbols from /usr/lib/beryl/libscreenshot.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libscreenshot.so
Reading symbols from /usr/lib/beryl/libstate.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/beryl/libstate.so

0xffffe410 in __kernel_vsyscall ()
(gdb) 

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e1d933 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7dc73c9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7c72be7 in crash_handler () from /usr/lib/beryl/libcrashhandler.so
#4  <signal handler called>
#5  0x0805e16b in keycodeToModifiers ()
#6  0x0805ea5e in eventLoop ()
#7  0x0805ab50 in main ()
Detaching from program: /usr/bin/beryl-xgl, process 5183

[CRASH_HANDLER]: "/tmp/beryl_crash-5183.out" created!

XGL Present
Initiating splash
```

Ouch, that was longer than I thought :) When I log into a normal gnome session, beryl-manager gives me an option that says 'Enable strict binding to prevent blank windows bug'. This is not available in the XGl session though. 

Now when I change to beryl as window manager, I see 'fatal I/O error' before a lot of scrolling text that starts with 'could not bind...' before the screen blanks out.

My card is Nvidia Geforce 4000 with 128MB.

I realise that Beryl is alpha software and crashes are expected. Should I file a bug report, and if so, where?

If anyone knows how to fix this issue, I'd really appreciate it, I like the Beryl demos ad would really love to try it out.

Cheers and good day,
David K

---

### Post by PriceChild on 2006-10-10
If i were you i would follow instructions from here: [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)
(That link was found here: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

You could always try #ubuntu-xgl on irc.freenode.net, or the official forums at [http://forum.beryl-project.org/](http://forum.beryl-project.org/) if you get no further help here.

---

