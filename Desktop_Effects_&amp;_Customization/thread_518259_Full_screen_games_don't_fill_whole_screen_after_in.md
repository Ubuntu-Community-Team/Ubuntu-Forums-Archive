---
title: "Full screen games don't fill whole screen after install XGL and for desktop effects"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Jamesbowden on 2007-08-05
I already posted this in General Help, but thinking about it, it may be better here. sorry.

I have followed this guide: [http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/](http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/)

so that I can enable desktop effects with my ATI Mobility Radeon 9600 M10

however after I logged back in, the desktop effects were working perfectly, but full screen (Sauerbraten and rRootage) games only display on a small box (640x420?) in the middle of an otherwise black screen.

does anyone know what the problem is an how I could fix it?

---

### Post by psyopper on 2007-08-05
The main problem is likely that you are trying to run a compositing manager (Beryl/Compiz) at the same time as you are trying to run an OpenGL game. Try disabling the desktop effects before starting your game.

---

### Post by jpereira on 2007-08-05
You might want to take a look at **[thread=518426]this thread[/thread]** on how to easily run a separate X just for a specific application, this overcoming the inability to run some 3D games in Xgl.

---

### Post by Jamesbowden on 2007-08-06
> **psyopper said:**
> The main problem is likely that you are trying to run a compositing manager (Beryl/Compiz) at the same time as you are trying to run an OpenGL game. Try disabling the desktop effects before starting your game.

That still doesn't solve the problem. and I am only running the built in Desktop Effects. not Beryl or Compiz Fusion 

> You might want to take a look at this thread on how to easily run a separate X just for a specific application, this overcoming the inability to run some 3D games in Xgl.

Taking a look at that thread now, thanks.

---

### Post by atomkarinca on 2007-08-06
i don't know exactly but desktop effects should be a different name for compiz.

---

