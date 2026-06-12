---
title: "afraid of installing xgl for effects"
date: 2008-02-14
forum: Desktop Effects &amp; Customization
---

### Post by pixelstuff on 2008-02-14
Hello all,
Yesterday, after messing my system up for a year, I made a new install. Everything is fresh now and uncluttered and all games that use glx work so far! I had lost all opengl after the gutsy upgrade. My graphic driver seems to be setup just fine - ati x600, proprietary enabled. 
BUT I get "desktop effect cannot be enabled". I had the effects before the fresh install and really want them back! Now after reading a lot in the forums it seems like I have to install XGL and that its on top of the x server and can mess up the 3d of games...
How come games can use opengl and compiz can't on my system? Do I really have to install xgl or is there something else that could be wrong? All compiz component are installed.
Thank you!!!

---

### Post by FuturePilot on 2008-02-14
Unfortunately if you're using the Restricted FGLRX ATI driver that is in the Ubuntu repos you need XGL in order for Compiz to work. The reason is that the FGLRX driver does not have the GLX_EXT_texture_from_pixmap extension that Compiz needs to function. Whereas a game would probably not use this extension. Therefore XGL is required to provide the acceleration. However I think if you use Envy you can get the latest FGLRX driver which does support AIGLX which will allow you to use Compiz without XGL.

---

### Post by pixelstuff on 2008-02-14
:( oh I see - thank you! I am wondering now if I should try to make two different sessions instead of messing with a working driver :confused:
 One more question: Is it safe to "try" xgl, can I uninstall it without pain?

---

### Post by FuturePilot on 2008-02-14
Yes, when you install XGL in Gutsy is runs a script to automatically set everything up. If it doesn't work out you can safely remove it.

---

### Post by pixelstuff on 2008-02-14
:) oh good! I am getting a stiff neck from moving around those rigid windows! thank you!

---

