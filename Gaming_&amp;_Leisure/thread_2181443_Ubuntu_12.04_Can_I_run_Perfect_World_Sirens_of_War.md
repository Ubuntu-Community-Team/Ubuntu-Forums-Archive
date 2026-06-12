---
title: "Ubuntu 12.04 Can I run Perfect World Sirens of War?"
date: 2013-10-17
forum: Gaming &amp; Leisure
---

### Post by ahears on 2013-10-17
I am running Ubuntu 12.04.03 LTS and have tried every post I can find on how to get PWI to run on linux but can't succeed. Does anyone know how to get Arc to install PWI on Ubuntu? I have installed latest versions of Playonlinux and Wine.

---

### Post by martialartist81 on 2013-10-18
I've seen that other folks have gotten Neverwinter Online to run; but I'm not sure about Arc.

[http://ubuntuforums.org/showthread.php?t=2153030](http://ubuntuforums.org/showthread.php?t=2153030)

Check that post as it walks you through getting Neverwinter to run; I assume it'll be close to the same for Sirens of War.... good luck and report your findings back!

---

### Post by ahears on 2013-10-22
Ok I got accomplished all of this in Playonlinux:


INSTALL PACKAGES TAB:


vcrun2005, vcrun2008, vcrun2010, vcrun6, d3dx9, d3dx10, d3dx11, dinput, dinput8, directmusic, directplay, directx9, dxfullsetup, fakeie6, ie6, msxml3, msxml4, msxml6, tahoma font, wininet.


DISPLAY TAB:


GLSL disabled
Direct Draw Renderer opengl
Video Memory Size "you video card memory here"
Off Screen Rendering Mode fbo
Render Target Lock Mode default
Multisampling Diasabled
Strict draw Ordering default


WINE TAB (and WINE TRICKS CONFIGURE WINE SETTINGS):


Windows version should be Windows XP under applications tab, under audio tab select "Default", check emulate virtual desktop and set to 1024x768 or whatever your desktop is set to, check the box to capture the Mouse.




WINE TRICKS CONFIGURE WINE SETTINGS:


Set "vertex shader to hardware" ENABLE, and check "allow pixel shader" also check emulate virtual desktop and set to 1024x768 or whatever your desktop is set to (I did this despite it being redundant... it works).


ARC RUNS and INSTALLS!!!
However Arc is asking for disk 2 of which there is no "Disk 2".

Therefore I am going to try to get PWI without ARC from this link "http://pwi-forum.perfectworld.com/showthread.php?t=1604141" and see if I can get it to run. 
Ok I have it installed but it crashed when I run the game. The game can't connect to the server online. Maybe something to do with my wine configuration that is blocking it and causing it to crash??

---

