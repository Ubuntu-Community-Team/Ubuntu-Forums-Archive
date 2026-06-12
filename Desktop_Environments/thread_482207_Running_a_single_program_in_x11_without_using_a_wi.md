---
title: "Running a single program in x11 without using a window manager"
date: 2007-06-23
forum: Desktop Environments
---

### Post by acobon on 2007-06-23
Here is my situation:
I wish to run a program inside x11 without a window manager. I am using ubuntu 7.04. I am trying to run a desktop enviroment called Athene, but it does not natively support my graphics card, but it can run inside of x11. It refuses to load piggy-backing off x11 since I can't get it to realize that it should use the configuration and drivers already in use with x11. So if I can't make it load x11 when it loads itself maybe it would be possible to load a barebones x11 shell and have it take over? How exactly would this be done?

---

### Post by raul_ on 2007-06-23
i'm not sure what you mean...

startx whatever_the_athene_launcher_is 

doesn't work?

---

### Post by acobon on 2007-06-24
Nope. And somehow I got my computer stuck to booting to the command line now. Whenever I  just type startx the gnome desktop starts to load but I wind-up with just a blan screen and the cursor. When I use startx and an application - say firefox - it justs quits and dumps me back to command prompt. The only way for me to access x11 at all is to go the fail-safe route (xinit) and from their access my programs. Is there a window manager that will allow me to configure it so that a program will launch full screen and stay in the background, completly? Without those annoying resize/title bar handles?

---

### Post by raul_ on 2007-06-24
you should edit your .xinitrc and comment the line that says "exec gdm" or something like that.

Then, next time you type startx, no DE should start (I think)

---

### Post by Poiema on 2007-10-30
> **acobon said:**
> Nope. And somehow I got my computer stuck to booting to the command line now. Whenever I  just type startx the gnome desktop starts to load but I wind-up with just a blan screen and the cursor. When I use startx and an application - say firefox - it justs quits and dumps me back to command prompt. The only way for me to access x11 at all is to go the fail-safe route (xinit) and from their access my programs. Is there a window manager that will allow me to configure it so that a program will launch full screen and stay in the background, completly? Without those annoying resize/title bar handles?

acobon - and anyone else who comes across this thread...... You should be able to access the Athene desktop by just entering Athene at the command prompt rather than startx. Athene is an alternative to x11 and although it can make use of x11 applications it can't be run at the same time as x11. If you have installed the Athene desktop correctly the prompt - Athene should boot what you are looking for. The Athene OS  website has more information for running their desktop from x11 (I think its an emulation mode that does not fully optimize the benefits of their desktop.). I know this is late, but hopefully it helps someone.

Poiema

---

