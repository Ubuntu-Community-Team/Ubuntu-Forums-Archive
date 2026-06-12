---
title: "Poss GDM issue: OpenGL reverts to mesa after logging out then in.(ATI fglrxinfo)"
date: 2007-01-09
forum: Desktop Environments
---

### Post by megadave on 2007-01-09
Hello all,

**Distro:**  Ubuntu 6.10 Edgy
**Vid Crd**: ATI Radeon X1600 Pro
**Driver**:  fglrx 8.28.8

Installed properly, works fine (poor performance in UT2004 / Q4 but that's par for the course)

When I initially log in after a restart, in the console, fglrxinfo gives me this:
[[IMG]http://img264.imageshack.us/img264/7259/fglrxinfofreshbootom6.th.png[/IMG]](http://img264.imageshack.us/my.php?image=fglrxinfofreshbootom6.png)

display: :0.0 screen: 0
OpenGL vendor string:  ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

and things run well.

If I log out/then log in w/o restarting then I get this (pls ignore typo):
[[IMG]http://img411.imageshack.us/img411/7494/fglrxinfologoutmw4.th.png[/IMG]](http://img411.imageshack.us/my.php?image=fglrxinfologoutmw4.png)
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I've just run the update utility and have everything updated as of Jan 9 2007 at 1am.

I've only seen a handful of threats around w/ the same problem but none were answered and were rather dated. I'm guessing the issue may also be with my xorg.conf so I'll attach it as well just in case.

Thanks for any help or insight.

---

### Post by lhardyl on 2008-02-18
[http://ubuntuforums.org/showthread.php?p=4358132]("http://ubuntuforums.org/showthread.php?p=4358132")

had the exact same problem and this seemed to solve it:)

---

