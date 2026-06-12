---
title: "Volume keys don't work in fullscreen applications..."
date: 2007-05-07
forum: Desktop Environments
---

### Post by GenPFault on 2007-05-07
I have the volume up/down keys on my multimedia keyboard set to turn the volume up/down in both Gnome and KDE.  Unfortunately, they don't seem to work in certain fullscreen applications like Planet Penguin Racer or ZSNES.  They do work in at least one fullscreen Wine app ([Warning Forever]("http://www18.big.or.jp/~hikoza/Prod/")).  What do I need to change to make this work?

---

### Post by merlyn on 2007-05-08
I can verify this, through experience.

The volume keys on my multimedia keyboard worked under Edgy when viewing multimedia content in fullscreen mode, but no longer work with Feisty.

Perhaps, there is a line in a config file to enable this, or even a key in GConf.

Any advice or suggestions would be most welcome.

Cheers.

---

### Post by GenPFault on 2007-05-09
> **merlyn said:**
> I can verify this, through experience.

The volume keys on my multimedia keyboard worked under Edgy when viewing multimedia content in fullscreen mode, but no longer work with Feisty.

Perhaps, there is a line in a config file to enable this, or even a key in GConf.

Any advice or suggestions would be most welcome.

Cheers.
Weird, volume keys worked for me by default (clean Feisty Kubuntu install) in fullscreen Mplayer, Kaffeine, and Totem-gstreamer.  Just not in fullscreen apps that like to capture input, like ppracer.  Which media player are you using?

EDIT: Just installed ubuntu-desktop and verified volume keys are still working in Totem and their ilk, and still not working in ppracer and ZSNES.  Either it's not a function of your desktop environment or the volume controls for both Gnome and KDE are equally broken.

---

### Post by merlyn on 2007-05-09
> **GenPFault said:**
> Weird, volume keys worked for me by default (clean Feisty Kubuntu install) in fullscreen Mplayer, Kaffeine, and Totem-gstreamer.  Just not in fullscreen apps that like to capture input, like ppracer.  Which media player are you using?

EDIT: Just installed ubuntu-desktop and verified volume keys are still working in Totem and their ilk, and still not working in ppracer and ZSNES.  Either it's not a function of your desktop environment or the volume controls for both Gnome and KDE are equally broken.

The app that I use for viewing 'video' is totem-xine, as it enables me to play DVD with menu support.

The volume keys stopped working in fullscreen mode after upgrading to Fiesty.

Cheers.

---

