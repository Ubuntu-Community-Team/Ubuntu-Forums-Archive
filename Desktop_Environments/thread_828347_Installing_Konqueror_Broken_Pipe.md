---
title: "Installing Konqueror: Broken Pipe?"
date: 2008-06-13
forum: Desktop Environments
---

### Post by Gannon8 on 2008-06-13
I was trying to install kubuntu-desktop using apt-get, but I ran across an error message:
```
Unpacking konqueror (from .../konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop', which is also in package kio-umountwrapper
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/konqueror_4%3a3.5.9-0ubuntu7.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It sort of looks like a problem with the server...

If this is in the wrong forum I apologies and ask mods to move it.

---

### Post by Gannon8 on 2008-06-16
bump

---

