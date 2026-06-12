---
title: "Beryl is installed but crashes when I try to use it.Radeon Mobility 9200"
date: 2007-03-17
forum: Desktop Effects &amp; Customization
---

### Post by s0n|k on 2007-03-17
Ok, so I followed this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I've installed beryl using this guide on another cpu and it works fine. This leads me to believe that its something wrong with my vid card. I'm using an ATI Radeon Mobility 9200. I can start with Beryl but when I try to do something in it, it crashes and takes me back to the login screen. Ive went through multiple posts and seen that most people request the output of the $fglrxinfo command. Here it is:

josh@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)


Any suggestions?

---

### Post by Waappu on 2007-03-18
Hi

Try to use AIGLX and open source driver

First uninstall XGL and fglrx driver.

See this page howto open suorce driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Guide for Beryl
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Upgrade to Xorg 7.2
Xorg 7.2 has enhanced AiGLX support and better 3D performance.
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

And here is my xorg.conf file for sample if you need
[http://koti.mbnet.fi/waappu/download/xorg.conf](http://koti.mbnet.fi/waappu/download/xorg.conf)

---

