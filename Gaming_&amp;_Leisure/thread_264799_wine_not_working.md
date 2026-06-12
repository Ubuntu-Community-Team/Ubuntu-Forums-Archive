---
title: "::wine not working?::"
date: 2006-09-25
forum: Gaming &amp; Leisure
---

### Post by feest on 2006-09-25
Hi, i've got a problem with wine, on the site of wine there is a nice index of games i should be able to run, i've tried very much of them but none of them seem to work? they all give erros like "no videomode specified" "no cd drive found" "acces violation at..." etc. how can i solve this? i'm quite new to wine so i don't know what to do. i've just downloaded it and installed... is there anything more to be done?

---

### Post by pay on 2006-09-25
Run winecfg then do to drives and click detect. Also make sure that you have your video drivers installed when trying to run games.

---

### Post by Tibor60 on 2006-09-25
I work with ubuntu for a couple of years already, and succeeded to solve rather different tasks...but I could never make work wine. Not in Breezy, not in Dapper. Now in Dapper when I try to config wine, I receive a bunch of error messages, and I can nothing to do with them. The 3D graphics work well in ubuntu, and ALSA is also functioning well. Maybe somebody have an idea what to do? (I tried to make work DVDDecrypter and DVDShrink as they have an extensive how-to in Ubuntu online... but no one works in my system)

tibor@GOLDEN10:~$ winecfg
wine: creating configuration directory '/home/tibor/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
wine: '/home/tibor/.wine' created successfully.
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please instal l this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory

---

