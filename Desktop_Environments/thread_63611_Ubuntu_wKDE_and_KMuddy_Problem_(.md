---
title: "Ubuntu w/KDE and KMuddy Problem :("
date: 2005-09-08
forum: Desktop Environments
---

### Post by CzarAlex on 2005-09-08
Hello.

I installed ubuntu hoary and then installed KDE from synaptic. Now, -all- I want to do is install kmuddy ([www.kmuddy.net)](www.kmuddy.net)). I had an error involving QT. i installed every package with QT in it **except** libqt3-dev because the package manager said i would have to uninstall the KDE package. Still no luck.

Finally i found on a website that someone had the similiar QT error (with another program) and used  
**./configure --with-qt-dir=/usr/share/qt3 --prefix=/usr** to fix it. I tried..and it seemed to get me past that point and finished ./configure ..

Now when i MAKE, This happens:

```
/usr/share/qt3/bin/moc ./dlgtimers.h -o dlgtimers.moc.cpp
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I/usr/X11R6/include   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -O2 -fno-exceptions -fno-check-new  -MT dlgtimers.moc.o -MD -MP -MF ".deps/dlgtimers.moc.Tpo" \
  -c -o dlgtimers.moc.o `test -f 'dlgtimers.moc.cpp' || echo './'`dlgtimers.moc.cpp; \
then mv -f ".deps/dlgtimers.moc.Tpo" ".deps/dlgtimers.moc.Po"; \
else rm -f ".deps/dlgtimers.moc.Tpo"; exit 1; \
fi
``` 

repeats on my screen everyone 10 or so seconds. I let it go for 15 minutes. 

Suggestions?  ](*,)

---

### Post by Mais on 2005-09-08
There are a few things involving packages such as qt that I have had to build as root. Try using sudo for both make and make install. The downside to this is it may cause you to only be able to run it as root, most likely not though.

---

### Post by CzarAlex on 2005-09-08
[QUOTE=Mais]There are a few things involving packages such as qt that I have had to build as root. Try using sudo for both make and make install. The downside to this is it may cause you to only be able to run it as root, most likely not though.[/QUOTE]

Thanks for the advice, but it didn't work.  :???:

---

