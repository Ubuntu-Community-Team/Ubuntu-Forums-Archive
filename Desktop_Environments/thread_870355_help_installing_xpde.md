---
title: "help installing xpde"
date: 2008-07-25
forum: Desktop Environments
---

### Post by dodle on 2008-07-25
Unfortunately there is no .deb file for [xpde]("http://xpde.com"), so I donwloaded the tarball and extracted it.  Apparently there is no compiling and I can get it to run by launching the file "startxpde".  But, I can't select it from the gdm login screen (because nothing is installed really).  How can I configure it so that I can select it from gdm?

---

### Post by Tim Sharitt on 2008-07-26
You will need to add a configuration file to /usr/share/xsessions (something like xpde.desktop for a file name) with the information needed to start xpde.
The file should look something like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=xpde
Exec=/usr/bin/startxpde
Type=Application
```

That should be enough to get it going from gdm.

---

