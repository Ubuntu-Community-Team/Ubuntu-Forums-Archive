---
title: "Shotcut help"
date: 2015-05-11
forum: Gaming &amp; Leisure
---

### Post by j-desanto0 on 2015-05-11
I've tried to install this and I keep getting this error.  Any ideas on how to get that?

[ATTACH=CONFIG]261949[/ATTACH]

---

### Post by efflandt on 2015-05-12
That seems to be installed by default in 14.04, unless you need a 32-bit version and/or something for wine:```
efflandt@XPS-8100-1404:~$ dpkg-query -l *sdl* | grep ii
ii  libsdl-image1.2:amd64                                 1.2.12-5build2                                         amd64        Image loading library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl1.2debian:amd64                                 1.2.15-8ubuntu1.1                                      amd64        Simple DirectMedia Layer
```

---

