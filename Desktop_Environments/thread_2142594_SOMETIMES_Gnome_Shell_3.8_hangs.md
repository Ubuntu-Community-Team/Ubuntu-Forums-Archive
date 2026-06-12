---
title: "SOMETIMES Gnome Shell 3.8 hangs"
date: 2013-05-06
forum: Desktop Environments
---

### Post by DisappearingOak on 2013-05-06
I'm on Raring with gnome-shell 3.8 installed via the Gnome 3 PPA (no other ppa installed, staging or otherwise). It works OK for the most part, but sometimes on a fresh boot, I log in to the desktop, and Gnome loads fine, but then I go to the overview, I see the wave but Gnome restarts, after that restart the gnome black panel shows up, but it hangs the X session and Gnome doesn't respond or restart but hangs X. This some happens on some boots but not all. Infrequently. The logs don't have any error, except xsesssion-errors has some stuff I can't understand. I'm on AMD hardware RS880 on Gigabyte 880-gm-d2h, enough ram 4gb.

.xsession-errors (there's no date or anything but it looks relevant):

```
Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
** Message: applet now removed from the notification area
      JS LOG: IBus version is too old
** Message: using fallback from indicator to GtkStatusIcon
    JS ERROR: !!!   Exception in callback for signal: sessions-loaded
    JS ERROR: !!!     message = '"No signal 'in-fullscreen-changed' on object 'MetaScreen'"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/layout.js"'
    JS ERROR: !!!     lineNumber = '226'
    JS ERROR: !!!     stack = '"()@/usr/share/gnome-shell/js/ui/layout.js:226
wrapper()@/usr/share/gjs-1.0/lang.js:213
()@/usr/share/gjs-1.0/lang.js:154
()@/usr/share/gjs-1.0/lang.js:248
_initializeUI()@/usr/share/gnome-shell/js/ui/main.js:134
_sessionsLoaded([object Object])@/usr/share/gnome-shell/js/ui/main.js:109
_emit("sessions-loaded")@/usr/share/gjs-1.0/signals.js:124
([object Object])@/usr/share/gnome-shell/js/ui/sessionMode.js:170
done()@/usr/share/gnome-shell/js/misc/fileUtils.js:33
([object GObject_Object],[object GObject_Object])@/usr/share/gnome-shell/js/misc/fileUtils.js:43
"'

** (nm-applet:1775): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
```


Any idea? Thanks.

---

### Post by markbl on 2013-05-06
Are you running any extensions? I have similar odd problems with GS 3.8 + GNOME 3 PPA on Ubuntu 13.04 when I was running the system-monitor extension. Disabled it and have not seen the problems since.

---

