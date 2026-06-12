---
title: "error kiba-dock plugins"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by Phil420 on 2008-01-08
every thing worked fine but when i write kiba-dock in the terminal, it says
```

phil@Phil-Desktop:~$ kiba-dock

** (kiba-dock:27542): WARNING **: Error (plugin.c @ line 205):
        '/usr/local/lib/kiba-dock/libdbus.so' is not loadable

```
what should i do?

Thanks!

---

### Post by Phil420 on 2008-01-08
now it does
```

phil@Phil-Desktop:~$ kiba-dock

** (kiba-dock:28328): WARNING **: Error (tray.c @ line 173):
        another systray already running



** (kiba-dock:28328): WARNING **: Error (plugin.c @ line 205):
        '/usr/local/lib/kiba-dock/libtray.so' is not loadable


Traceback (most recent call last):
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 6, in <module>
    import feedparser
ImportError: No module named feedparser

```

any idea??

---

