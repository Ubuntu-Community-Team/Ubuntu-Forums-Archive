---
title: "Age of Empires II on vmware player = poor mouse performance"
date: 2006-09-21
forum: Gaming &amp; Leisure
---

### Post by zapcojake on 2006-09-21
I am using Dapper with the latest repo k7 kernel, Gnome, Copmiz from the repos, Vmware player with vmware tools installed, AOE installs and starts ok but the mouse is jekry, slow and unpredictable.  Has anyone else tried this or had similar trouble?  I have an ATI IXP chipset with onboard video.

---

### Post by Abild on 2006-09-21
AOE works quite good under WINE. So that solution would be my first choice. The fact that you are using xgl may cause problems when running games. This [ howto](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=nonXgl) will help you with running games in a standard Xorg server from Xgl.

If you have to use vmware [Enabling 3d acceleration](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html) might be a good idea. To solve the mouse issues try disable  the option which makes it possible for the mouse cursor to leave the vmware window when you move it to the edge (makes sense?)

You should be aware that vmware is not made for games. Their Direct3c implementation is not much more complete than wines and games played in vmware will have a huge performance loss. In 3dmark 01 i only get 25% of the performance i get in windows. The performance of wine is much closer to windows.

---

### Post by rastilin on 2006-09-21
There's only two things I can think to suggest. 

1. It could be an AOE2 bug. I've had reams of issues with that program. So a video issue wouldn't surprise me.

2. Try doing it without xgl, if it's an .Xsession file, you should toggle it just to check. I've also had problems getting other opengl programs playing nicely with xgl.

---

