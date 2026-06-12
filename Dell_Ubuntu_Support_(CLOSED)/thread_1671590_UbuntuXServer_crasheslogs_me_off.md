---
title: "Ubuntu/XServer crashes/logs me off"
date: 2011-01-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by someusername on 2011-01-20
Hi,

After some indeterminate amount of time I experience a sudden termination of all my processes, killing of the desktop environment - gnome - and a revert to the log in screen.

I'm using the proprietary ATi drivers for "1 GB GDDR5 for ATI FirePro M7820". The machine is a dell M6500 with 8GB of memory, with a resolution of 1920x1200 on two screens. The second screen is connected through VGA. Both are turned on at the same time. The default of ubuntu are otherwise running, nothing customized. I assume this means I'm using compiz.

```
$ uname -a
Linux catamorphism 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010
```

...

As I was typing the above, the mouse buttons stopped working and I couldn't select this field again. I had to reboot.

...

I would like some help to resolve this.

Cheers

Edit - some logs that might help from ~/.xsession_errors.old:

```
###!!! ABORT: X_CloseDevice: XI_BadDevice (invalid Device parameter); 11 requests ago: file nsX11ErrorHandler.cpp, line 182
_XError+0x000000F4 [/usr/lib/libX11.so.6 +0x00043E24]
UNKNOWN [/usr/lib/libX11.so.6 +0x0004A30C]
_XReply+0x00000140 [/usr/lib/libX11.so.6 +0x0004A9B0]
XSync+0x00000063 [/usr/lib/libX11.so.6 +0x0003E333]
XCloseDisplay+0x00000080 [/usr/lib/libX11.so.6 +0x0001CE50]
UNKNOWN [/usr/lib/libgdk-x11-2.0.so.0 +0x000509E6]
g_object_unref+0x00000174 [/usr/lib/libgobject-2.0.so.0 +0x00010A24]
UNKNOWN [/usr/lib/firefox-3.6.13/libxul.so +0x004CE648]
XRE_main+0x000034FD [/usr/lib/firefox-3.6.13/libxul.so +0x004D3060]
UNKNOWN [/usr/lib/firefox-3.6.13/firefox-bin +0x00001FA1]
__libc_start_main+0x000000FE [/lib/libc.so.6 +0x0001ED8E]
UNKNOWN [/usr/lib/firefox-3.6.13/firefox-bin +0x00001C89]

snip

(nautilus:1954): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:1954): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 15 elements at quit time
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'crashreporter' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 29626 requests (29625 known processed) with 0 events remaining.

```

---

### Post by someusername on 2011-01-22
bmp

---

### Post by someusername on 2011-01-27
bmp

---

