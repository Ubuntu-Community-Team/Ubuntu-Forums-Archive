---
title: "[SOLVED] missing title and window borders with Compiz Fusion"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by caffienefree on 2007-10-27
Hi all,

I've been trying to get compiz fusion working again this weekend using information online, but I'm really going nowhere fast. The issue is that starting compiz results in windows without borders/title bars, and the application bar is no longer operational. I have Ubuntu 7.10 running on a dell latitude D520, Intel 945 onboard graphics.

Beryl (AiGLX) ran fine under edgy and Compiz worked when I had it installed in feisty. I upgraded to gutsy... I suppose mid-september? It hasn't worked since then, so I got used to unwobbly windows...

So, some information/processes that I've already gone through.

:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

:~$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

glxinfo tells me that direct rendering is off, but starting compiz by LIBGL_ALWAYS_INDIRECT=1 compiz --replace & gives the same result anyway.

On a suggestion that I found, I tried the following, but the same issue resulted:
LD_LIBRARY_PATH=/usr/lib compiz --replace gconf &

Verbose output from glxinfo:
:~$ LIBGL_DEBUG=verbose glxinfo -i
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
display: :0  screen: 0
direct rendering: No (-i specified)

Trying to load emerald prints the following, even though libwnck22 is installed:
emerald: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

Also attached is my xorg.conf file.

I'd appreciate any help or suggestions in this matter. I'm a little confused with it all right now... :confused:

---

### Post by caffienefree on 2007-10-27
So, progress.

After reading a thread in the forum, I added skip_checks=yes to what I was already doing, so...

LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 SKIP_CHECKS=yes compiz --replace --indirect-rendering --sm-disable ccp &

...doesn't render the title bar/border, but now the application bar works and minimize/maximize effects (magic lamp) work, as well at the alt-tab switcher, right hand hot point, etc. Like I said, progress!

---

### Post by caffienefree on 2007-10-27
Okay, this thread ([http://ubuntuforums.org/showthread.php?t=579884](http://ubuntuforums.org/showthread.php?t=579884)) gave the final key for fixing emerald... compiz works! Hurrah!

sudo ln -sf /usr/lib/libwnck-1.so /usr/lib/libwnck-1.so.18 fiixed "error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory".

---

