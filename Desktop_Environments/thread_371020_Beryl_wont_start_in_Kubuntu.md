---
title: "Beryl wont start in Kubuntu"
date: 2007-02-26
forum: Desktop Environments
---

### Post by evkefalas on 2007-02-26
Hi I have Kubunty 6.10
ATI RADEON 9600 drivers installed:

evan@evan-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

evan@evan-laptop:~$ glxinfo | grep direct
direct rendering: Yes

Beryl Installed properly, following how to
starts ok but when i select from select window manager  the beryl option
it crashes back to the default KDE environment

Can anyone please help?
Many Thanks

---

### Post by jamboarder on 2007-02-26
If you have translucency/shadows enabled in the KDE window manager (kwin) try disabling them.  Additionally under the beryl manager right click menu try selecting no fallback window manager instead of kwin.

good luck!

---

### Post by evkefalas on 2007-02-27
tried that but nothing changes :(
any ideas?

---

### Post by evkefalas on 2007-02-28
its like the beryl crashes and falls back in the kde enviroment

if i login from xgl session everything is very very small and slowwwww
and when u start beryl you can rotate the cube  but is white blanc from all sides and u cant do anything

can someone pleaseeee help

---

