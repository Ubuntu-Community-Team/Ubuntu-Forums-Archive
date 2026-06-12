---
title: "Opera &amp; undefined symbol: XkbSetPerClientControls"
date: 2006-01-13
forum: Desktop Environments
---

### Post by andguent on 2006-01-13
I've spent about 2-3 hours searching for a solution for this. I wish I knew what happened immediately before this started, but I don't. I had Opera working successfully for a good month on this **Breezy** box.

When I run opera, this is the message I get:
```

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls

```

There are many hits for the first two lines that point to JVM issues. However, googling for the last line (and parts of it) shows little that is useful. I would post to the Opera forums, but I have the feeling that XkbSetPerClientControls is an X11/Gnome thing.

For the fun of it, I uninstalled and reinstalled java-common and libqt3-mt. I've tried running opera from installing both 
opera_8.50-20050916.6-shared-qt_en_etch_i386.deb and 
opera_8.51-20051114.6-shared-qt_en_etch_i386.deb. 
Same result.

Any ideas welcomed. More info can be dumped here easily if needed. Thanks.

-----
Why offend Microsoft with insults when you can offend them by using Debian?

---

### Post by andguent on 2006-01-14
I tried doing some debugging using opera switches. No result.

```
root@akita:~# opera -debugfont
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls
root@akita:~# opera -debugjava
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls
root@akita:~# opera -debugkeyboard
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls
root@akita:~# opera -debugmouse
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls
root@akita:~# opera -debugplugin
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls

```

---

### Post by andguent on 2006-01-15
Apparently skype does the same thing. I guess I need to look further into libqt. Any ideas welcomed.

```
skype: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: XkbSetPerClientControls
```

---

### Post by andguent on 2006-02-25
It's been a while, and still no result. It's probably related that there are also difficulties running apps that start with X (like xterm, xtightvncviewer). I get this:


xterm: symbol lookup error: /usr/lib/libXaw7.so.7: undefined symbol: XmuCvtGravityToString

xtightvncviewer: symbol lookup error: /usr/lib/libXaw7.so.7: undefined symbol: XmuCvtGravityToString

Research on these messages shows a good deal of hits, but I havin't found any results yet. I tried apt-get install --reinstall libc5 libc6 for good measure, but no result.

Ideas very welcomed.

---

