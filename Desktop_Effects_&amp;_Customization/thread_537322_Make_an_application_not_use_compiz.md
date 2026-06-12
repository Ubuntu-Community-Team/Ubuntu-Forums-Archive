---
title: "Make an application not use compiz"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by amrlima on 2007-08-28
Is there a way to make an application nor to use compiz as the window manager and use metacity instead? I want to play a game with wine and performance is poor with compiz active :(. Tanks!!

---

### Post by psyopper on 2007-08-28
Compiz as the window manager IS an OpenGL application. Having it ignore WINE will not resolve the fact that it is still making OpenGL calls to the video card to render the rest of your desktop, regardless of if you can see your desktop or not.

The way around this is to manually turn Compiz off before launching your game. There are a number of scripts floating around on this forum (check the Gaming section) to semi-automate this task. Talk in the Compiz development community is for it to become a complete Desktop Environment (rather than just a Window Manager like it is now), and part of that development includes automatic reduction of *GL overhead when other *GL apps are running.

---

