---
title: "World of Warcraft Starting up error"
date: 2005-07-08
forum: Gaming &amp; Leisure
---

### Post by Barth on 2005-07-08
I've installed Cedega through the cvs, everything went fine. Installed World of Warcraft. Patched world of warcraft to 1.30(with a patch I already downloaded on my windows partition) So I never had ran WoW.exe yet. 

Here's a screenshot of my window when I started up WoW.exe: [http://home.quicknet.nl/mw/prive/gvdhoek/error.png](http://home.quicknet.nl/mw/prive/gvdhoek/error.png)
I can't really do anything with it, so I press escape. and then I get the following error:
[http://home.quicknet.nl/mw/prive/gvdhoek/Screenshot.png](http://home.quicknet.nl/mw/prive/gvdhoek/Screenshot.png).

I installed the fglrx driver, and got opengl working(tested it with fgl_glxgears, and glxgears)

I hope some of you got an idea, cause I am out of any.

---

### Post by Barth on 2005-07-09
[QUOTE=Barth]I've installed Cedega through the cvs, everything went fine. Installed World of Warcraft. Patched world of warcraft to 1.30(with a patch I already downloaded on my windows partition) So I never had ran WoW.exe yet. 

Here's a screenshot of my window when I started up WoW.exe: [http://home.quicknet.nl/mw/prive/gvdhoek/error.png](http://home.quicknet.nl/mw/prive/gvdhoek/error.png)
I can't really do anything with it, so I press escape. and then I get the following error:
[http://home.quicknet.nl/mw/prive/gvdhoek/Screenshot.png](http://home.quicknet.nl/mw/prive/gvdhoek/Screenshot.png).

I installed the fglrx driver, and got opengl working(tested it with fgl_glxgears, and glxgears)

I hope some of you got an idea, cause I am out of any.[/QUOTE]
 Alright, I know the problem now, the cedega I had didnt support the latest directx. As I also got the warning when installing World of warcraft that directx wasn't installed. A friend gave me an already compiled .deb package, and I reinstalled cedega. Everything works fine now.

---

