---
title: "Metacity issues"
date: 2009-12-16
forum: Desktop Environments
---

### Post by Gandalf_the_Grey on 2009-12-16
In GNOME, if I turned the desktop effects on before, everything worked great.  Now, however, for some unknown reason, whenever I turn the effects on, Metacity dies.  I lose all the windows' frames, so I can't move any windows, Cairo-Dock becomes a white box, and my terminal window turns white with no text, and if I blindly type 'metacity' or 'metacity --replace' nothing happens.  With no effects, everything works fine.  However, I would like my effects back.  Reinstalling metacity and metacity-common has no effect.  Another interesting side effect-my System Settings thing in the Kickstart menu under KDE disappeared, as did my effects for KDE. However, KDE's window manager works just fine.

CompizCheck report:

```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

Hmmm.  It only happens when I enable Compiz.  I tried reinstalling compiz, also with no results.

Now I've tried reinstalling Compiz and Metacity by completely removing through Synaptic, then reinstalling.  No luck.  I also purged all my GNOME settings, and nothing happened then either.  Solutions would be muchly appreciated.

---

