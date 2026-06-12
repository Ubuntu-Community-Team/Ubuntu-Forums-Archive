---
title: "what are the advantages of Xgl"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by ZeldaFan on 2007-08-04
I have beryl set up to run on a gnome Xgl session and gnome without Xgl (I guess its a xorg session). What's the advantages of running an xgl session as opposed to one without it. I haven't really noticed any performance boosts, beryl still runs the same, and it takes at least 100 more MB of my RAM.

---

### Post by nicolas2b on 2007-08-04
If you can use beryl without XGL, DO IT !!
Xgl is for people who can't use AIGLX (for example with some ATI cards). Xgl is bad, slow for the computer ...

---

### Post by ZeldaFan on 2007-08-04
what is aiglx, should I be using that instead?

---

### Post by nicolas2b on 2007-08-04
> **ZeldaFan said:**
> what is aiglx
From wikipedia:
Accelerated Indirect GLX ("AIGLX") is an open source project founded by Red Hat and the Fedora Linux community to allow accelerated indirect GLX rendering capabilities to X.org and DRI drivers. This allows remote X clients to get fully hardware accelerated rendering over the GLX protocol; coincidentally, this development was required for OpenGL compositing window managers (such as Compiz or Beryl) to function with hardware acceleration.

> **ZeldaFan said:**
>  should I be using that instead?
Yes, it's better, you have not to lauch an extra program and your video card is made for.

---

### Post by the yawner on 2007-08-04
Function wise, they are just the same. But from what I gather:
- Nvidia proprietary drivers and ATI open srouce drivers work with AIGLX
- ATI proprietary drivers do not support AIGLX and thus you'll need to enable XGL

I'm using a Thinkpad which has an ATI video card and I've tried both routes to run Compiz/Beryl. However, I found that running XGL + proprietary driver worked a lot better for this machine than the one using the open source driver.

I also have a desktop which on the other hand has an Nvidia video card. Installed the proprietary driver and from there everything worked fine with Compiz/Beryl.

---

### Post by ZeldaFan on 2007-08-04
Well, I previously followed a guide to set up beryl with Xgl. How do I get aiglx running? Most guides just tell me how to get Aiglx running with beryl together. I tried to follow one using only the steps that applied to changing my xorg.file to get Aiglx set up, but I got a xorg error when restarting. Luckily I backed up my xorg.conf file

---

