---
title: "Firefox 20"
date: 2006-11-04
forum: Desktop Environments
---

### Post by ubman on 2006-11-04
Hi All
i have just d-loaded firefox 20 extracted it to my home
created launcher on desktop all is good execpt plugins
not working could someone help me with this?
      Thanks Rick

---

### Post by jbtito03 on 2006-11-04
Hi!

They will not work until updates for them come out as they r not compatible with firefix 2.0

Firefox should check if updates r available and when they r he updates them and turns them on :D

Cheers...

Jb

---

### Post by ubman on 2006-11-04
> **jbtito03 said:**
> Hi!

They will not work until updates for them come out as they r not compatible with firefix 2.0

Firefox should check if updates r available and when they r he updates them and turns them on :D

Cheers...

Jb

bummer](*,)  thanks for the reply though!

---

### Post by mister_p_1998 on 2006-11-06
> **ubman said:**
> Hi All
i have just d-loaded firefox 20 extracted it to my home
created launcher on desktop all is good execpt plugins
not working could someone help me with this?
      Thanks Rick

Install nightly-1.1.xpi plugin, this will force plugin compatiblity. Works for me with no problems.

---

### Post by RikoW on 2006-11-06
> **jbtito03 said:**
> Hi!

They will not work until updates for them come out as they r not compatible with firefix 2.0



I don't think that is entirely true! It is probably true for most extensions, but many plugins (like acrobat, openoffice, realplay etc) should work just fine. I just made sym-links from the "old" firefox plugin directory to the 2.0 plugin dir:

```
> cd /opt/firefox2/plugins
> ls -l
total 20
lrwxrwxrwx 1 root     root        40 2006-10-19 21:01 flashplayer.xpt -> /usr/lib/mozilla/plugins/flashplayer.xpt
lrwxrwxrwx 1 root     root        41 2006-10-19 21:01 kaffeineplugin.a -> /usr/lib/mozilla/plugins/kaffeineplugin.a
lrwxrwxrwx 1 root     root        42 2006-10-19 21:01 kaffeineplugin.la -> /usr/lib/mozilla/plugins/kaffeineplugin.la
lrwxrwxrwx 1 root     root        42 2006-10-19 21:01 kaffeineplugin.so -> /usr/lib/mozilla/plugins/kaffeineplugin.so
lrwxrwxrwx 1 root     root        42 2006-10-19 21:01 libflashplayer.so -> /usr/lib/mozilla/plugins/libflashplayer.so*
lrwxrwxrwx 1 root     root        45 2006-10-19 21:01 libjavaplugin_oji.so -> /usr/lib/mozilla/plugins/libjavaplugin_oji.so
-rwxr-xr-x 1 wichmann wichmann 19160 2006-10-19 09:18 libnullplugin.so*
lrwxrwxrwx 1 root     root        46 2006-10-19 21:05 libunixprintplugin.so -> /usr/lib/firefox/plugins/libunixprintplugin.so
lrwxrwxrwx 1 root     root        35 2006-10-19 21:05 nphelix.so -> /usr/lib/firefox/plugins/nphelix.so
lrwxrwxrwx 1 root     root        36 2006-10-19 21:05 nphelix.xpt -> /usr/lib/firefox/plugins/nphelix.xpt*
lrwxrwxrwx 1 root     root        33 2006-10-19 21:01 nppdf.so -> /usr/lib/mozilla/plugins/nppdf.so

```

Note, that I installed FF2.0 in /opt and use the plugins in the directories /usr/lib/mozilla and /usr/lib/firefox

Cheers,

                   Riko

---

