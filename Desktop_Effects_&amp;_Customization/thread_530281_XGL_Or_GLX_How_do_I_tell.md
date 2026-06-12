---
title: "XGL Or GLX How do I tell?"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by RandomUsr on 2007-08-20
I want to know whether I'm using XGL or GLX, I'm quite certain it's GLX, But I want to know for sure because I hope to use Avant window manger with the KIBA Dock.

PS?

Does Avant run side by side with other window managers or instead of? and secondly, is the Kiba dock a seperate Object or an enhancement to Avant?

---

### Post by Jouke74 on 2007-08-20
Ehm start here: [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

And here: [http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)

You might also want to check : [http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

XGL (server) is a program that runs on top of your standard Xorg server and makes the use of OpenGL extensions possible. Note that this is only useful for owners of ATI cards with >R400. 

GLX is a module that can be started from your graphics card driver and that allows for the OpenGLto run (independent of the XGL / Xorg server). This is required for all videocards.

---

### Post by RandomUsr on 2007-08-20
So by that thought process, I should have no trouble installing Avant and the kiba dock?

---

### Post by Rupertronco on 2007-08-21
Avant and kiba dock essentially do the same thing, you won't want both of them. Do you already have a compositing manager(beryl or compiz) installed? They are required for both of the docks you mentioned. 

As far as no trouble installs on the docks, they're pretty straightforward, the compositing applications are a whole different beast. What type of system/graphics card are you using?

---

