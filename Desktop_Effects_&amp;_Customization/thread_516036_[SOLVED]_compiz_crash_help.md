---
title: "[SOLVED] compiz crash help"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2007-08-02
i had compiz fusion working fine, but for some reason it crashes when i run 'compiz --replace'. here is the output:

```
compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugin bench (bench)
Adding plugin keybinding (keybinding)
Adding plugin mousegestures (mousegestures)
Adding plugin blur (blur)
Adding plugin minimize (minimize)
Adding plugin neg (neg)
Adding plugin gears (gears)
Adding plugin scalefilter (scalefilter)
Adding plugin addhelper (addhelper)
Adding plugin cubecaps (cubecaps)
Adding plugin thumbnail (thumbnail)
Adding plugin zoom (zoom)
Adding plugin wobbly (wobbly)
Adding plugin ring (ring)
Adding plugin scale (scale)
Adding plugin screensaver (screensaver)
Adding plugin regex (regex)
Adding core settings (General Options)
Adding plugin wall (wall)
Adding plugin flash (flash)
Adding plugin firepaint (firepaint)
Adding plugin video (video)
Adding plugin quickchange (quickchange)
Adding plugin workarounds (workarounds)
Adding plugin vpswitch (vpswitch)
Adding plugin place (place)
Adding plugin visualevent (visualevent)
Adding plugin shift (shift)
Adding plugin winrules (winrules)
Adding plugin reflex (reflex)
Adding plugin glib (glib)
Adding plugin dbus (dbus)
Adding plugin opacify (opacify)
Adding plugin extrawm (extrawm)
Adding plugin cheatsheet (cheatsheet)
Adding plugin clone (clone)
Adding plugin decoration (decoration)
Adding plugin group (group)
Adding plugin ezoom (ezoom)
Adding plugin 3d (3d)
Adding plugin splash (splash)
Adding plugin screenshot (screenshot)
Adding plugin plane (plane)
Adding plugin water (water)
Adding plugin put (put)
Adding plugin inotify (inotify)
Adding plugin wallpaper (wallpaper)
Adding plugin animation (animation)
Adding plugin fs (fs)
Adding plugin showdesktop (showdesktop)
Adding plugin resize (resize)
Adding plugin fade (fade)
Adding plugin move (move)
Adding plugin svg (svg)
Adding plugin expo (expo)
Adding plugin notification (notification)
Adding plugin crashhandler (crashhandler)
Adding plugin mblur (mblur)
Adding plugin kiosk (kiosk)
Adding plugin rotate (rotate)
Adding plugin annotate (annotate)
Adding plugin png (png)
Adding plugin gotovp (gotovp)
Adding plugin resizeinfo (resizeinfo)
Adding plugin imgjpeg (imgjpeg)
Adding plugin colorfilter (colorfilter)
Adding plugin atlantis (atlantis)
Adding plugin scaleaddon (scaleaddon)
Adding plugin fadedesktop (fadedesktop)
Adding plugin switcher (switcher)
Adding plugin cubereflex (cubereflex)
Adding plugin widget (widget)
Adding plugin snap (snap)
Adding plugin cube (cube)
Adding plugin text (text)
Adding plugin trailfocus (trailfocus)
Initializing core options...done
Initializing thumbnail options...done
Initializing zoom options...done
Initializing workarounds options...done
Initializing vpswitch options...done
Initializing place options...done
Initializing shift options...done
Initializing extrawm options...done
Initializing cheatsheet options...done
Initializing decoration options...done
inotify_add_watch: No such file or directory

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:6522): Wnck-WARNING **: Unhandled action type (nil)
Initializing animation options...done
fuse: failed to exec fusermount: No such file or directory
Initializing fs options...done
Initializing showdesktop options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing mblur options...done
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 6520
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libGLcore.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libgconf-2.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1222973200 (LWP 6520)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libthumbnail.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libzoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libshift.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libglib.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libextrawm.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libcheatsheet.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcheatsheet.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libinotify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/libfs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfs.so
Reading symbols from /usr/lib/libfuse.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfuse.so.2
Reading symbols from /usr/lib/compiz/libshowdesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found).Undefined command: "-e".  Try "help".
..done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libmblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so

(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1222973200 (LWP 6520)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bef6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b96a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb374c982 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe426e8 in ?? ()
#5  0xb374cab4 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe4498f in ?? ()
#7  0x00001978 in ?? ()
#8  0x00001978 in ?? ()
#9  0x00001978 in ?? ()
#10 0xbfe426f8 in ?? ()
#11 0xb7de5340 in xmlXPathRegisterAllFunctions () from /usr/lib/libxml2.so.2
#12 <signal handler called>
#13 0xb38c0f1b in cairo_set_line_width () from /usr/lib/libcairo.so.2
#14 0xb3741790 in ?? () from /usr/lib/compiz/libresizeinfo.so
#15 0x00000002 in ?? ()
#16 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bef6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b96a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb374c982 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe426e8 in ?? ()
#5  0xb374cab4 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe4498f in ?? ()
#7  0x00001978 in ?? ()
#8  0x00001978 in ?? ()
#9  0x00001978 in ?? ()
#10 0xbfe426f8 in ?? ()
#11 0xb7de5340 in xmlXPathRegisterAllFunctions () from /usr/lib/libxml2.so.2
#12 <signal handler called>
#13 0xb38c0f1b in cairo_set_line_width () from /usr/lib/libcairo.so.2
#14 0xb3741790 in ?? () from /usr/lib/compiz/libresizeinfo.so
#15 0x00000002 in ?? ()
#16 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 6520

[CRASH_HANDLER]: "/tmp/compiz_crash-6520.out" created!
```

here is "/tmp/compiz_crash-6520.out"

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 6520
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libSM.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /usr/lib/libXcursor.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libGLcore.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libgconf.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libgconf.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/libgconf-2.so.4...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgconf-2.so.4
Reading symbols from /usr/lib/libORBit-2.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libORBit-2.so.0
Reading symbols from /usr/lib/libgthread-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgthread-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/librt.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/librt.so.1
Reading symbols from /usr/lib/libgobject-2.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgobject-2.0.so.0
Reading symbols from /usr/lib/libglib-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libglib-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libpthread.so.0...
(no debugging symbols found)...done.
[Thread debugging using libthread_db enabled]
[New Thread -1222973200 (LWP 6520)]
Loaded symbols for /lib/tls/i686/cmov/libpthread.so.0
Reading symbols from /usr/lib/libgmodule-2.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libgmodule-2.0.so.0
Reading symbols from /lib/tls/i686/cmov/libnss_compat.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_compat.so.2
Reading symbols from /lib/tls/i686/cmov/libnsl.so.1...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnsl.so.1
Reading symbols from /lib/tls/i686/cmov/libnss_nis.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_nis.so.2
Reading symbols from /lib/tls/i686/cmov/libnss_files.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libnss_files.so.2
Reading symbols from /usr/lib/compiz/libthumbnail.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libthumbnail.so
Reading symbols from /usr/lib/compiz/libzoom.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libzoom.so
Reading symbols from /usr/lib/compiz/libregex.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libregex.so
Reading symbols from /usr/lib/compiz/libworkarounds.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libworkarounds.so
Reading symbols from /usr/lib/compiz/libvpswitch.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libvpswitch.so
Reading symbols from /usr/lib/compiz/libplace.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libplace.so
Reading symbols from /usr/lib/compiz/libshift.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/libpangocairo-1.0.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangocairo-1.0.so.0
Reading symbols from /usr/lib/libpango-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpango-1.0.so.0
Reading symbols from /usr/lib/libcairo.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcairo.so.2
Reading symbols from /usr/lib/libpangoft2-1.0.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpangoft2-1.0.so.0
Reading symbols from /usr/lib/libfontconfig.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfontconfig.so.1
Reading symbols from /usr/lib/libfreetype.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfreetype.so.6
Reading symbols from /usr/lib/libexpat.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libexpat.so.1
Reading symbols from /usr/lib/compiz/libglib.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libglib.so
Reading symbols from /usr/lib/compiz/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libextrawm.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libextrawm.so
Reading symbols from /usr/lib/compiz/libcheatsheet.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcheatsheet.so
Reading symbols from /usr/lib/compiz/libdecoration.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdecoration.so
Reading symbols from /usr/lib/libdecoration.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdecoration.so.0
Reading symbols from /usr/lib/compiz/libinotify.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libinotify.so
Reading symbols from /usr/lib/compiz/libanimation.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libanimation.so
Reading symbols from /usr/lib/compiz/libfs.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libfs.so
Reading symbols from /usr/lib/libfuse.so.2...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libfuse.so.2
Reading symbols from /usr/lib/compiz/libshowdesktop.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshowdesktop.so
Reading symbols from /usr/lib/compiz/libresize.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libmove.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmove.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libmblur.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libmblur.so
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/compiz/libresizeinfo.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresizeinfo.so

(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
(gdb) (gdb) 
Thread 1 (Thread -1222973200 (LWP 6520)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bef6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b96a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb374c982 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe426e8 in ?? ()
#5  0xb374cab4 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe4498f in ?? ()
#7  0x00001978 in ?? ()
#8  0x00001978 in ?? ()
#9  0x00001978 in ?? ()
#10 0xbfe426f8 in ?? ()
#11 0xb7de5340 in xmlXPathRegisterAllFunctions () from /usr/lib/libxml2.so.2
#12 <signal handler called>
#13 0xb38c0f1b in cairo_set_line_width () from /usr/lib/libcairo.so.2
#14 0xb3741790 in ?? () from /usr/lib/compiz/libresizeinfo.so
#15 0x00000002 in ?? ()
#16 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
(gdb) 
(gdb) 
(gdb) #0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bef6a3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b96a3f in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb374c982 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbfe426e8 in ?? ()
#5  0xb374cab4 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbfe4498f in ?? ()
#7  0x00001978 in ?? ()
#8  0x00001978 in ?? ()
#9  0x00001978 in ?? ()
#10 0xbfe426f8 in ?? ()
#11 0xb7de5340 in xmlXPathRegisterAllFunctions () from /usr/lib/libxml2.so.2
#12 <signal handler called>
#13 0xb38c0f1b in cairo_set_line_width () from /usr/lib/libcairo.so.2
#14 0xb3741790 in ?? () from /usr/lib/compiz/libresizeinfo.so
#15 0x00000002 in ?? ()
#16 0x00000000 in ?? ()
(gdb) The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 6520
```

what's causing the crash?

---

### Post by dbbolton on 2007-08-02
i figured that this was caused by my xorg.conf file. i reconfigured it according to [http://compiz.org/NVidia](http://compiz.org/NVidia) and it's fine now :)

---

