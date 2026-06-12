---
title: "Applets crashing"
date: 2010-05-05
forum: Desktop Environments
---

### Post by lashi on 2010-05-05
Any idea why applets keep crashing after upgrade to Lucid? It's very annoying, especially nm-applet. There's a complaint in dmesg output too:

[93096.347484] sensors-applet[24152]: segfault at 1332f30 ip 011b5704 sp bfa861d0 error 4 in libgtk-x11-2.0.so.0.2000.0[f4f000+3cd000]
[98383.009186] sensors-applet[24609]: segfault at 135bf30 ip 011de704 sp bfdfa580 error 4 in libgtk-x11-2.0.so.0.2000.0[f78000+3cd000]

[132227.008333] sensors-applet[31232]: segfault at 127df30 ip 01100704 sp bfc8ac20 error 4 in libgtk-x11-2.0.so.0.2000.0[e9a000+3cd000]
[133822.686820] xchat[31773]: segfault at ffe1bfe8 ip 0034a3ff sp bfd0a6fc error 4 in libgobject-2.0.so.0.2400.0[32a000+3d000]

[140033.300607] nm-applet[22928] general protection ip:aac3e4 sp:bf8d53bc error:0 in libgtk-x11-2.0.so.0.2000.0[a55000+3cd000]

[142668.004187] sensors-applet[32028]: segfault at 13acf30 ip 0122f704 sp bfe70dc0 error 4 in libgtk-x11-2.0.so.0.2000.0[fc9000+3cd000]

[168764.136789] sensors-applet[1511]: segfault at 129bf30 ip 0111e704 sp bfde89d0 error 4 in libgtk-x11-2.0.so.0.2000.0[eb8000+3cd000]

Etc.

---

### Post by tomate22 on 2010-05-17
hi folks,

I have the same problem with the "indicator-applet" ... 
Error Message:

kernel: [ 4132.916543] indicator-apple[20447]: segfault at 2c ip 002dfcaf sp bfb0aa10 error 4 in libgtk-x11-2.0.so.0.2000.0[19e000+3cd000]

any idea?

---

