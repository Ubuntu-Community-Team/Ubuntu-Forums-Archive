---
title: "AIGLX/XGL with radeon driver?"
date: 2006-10-31
forum: Desktop Environments
---

### Post by eClaW on 2006-10-31
Heys guy,

I've got a A31P notebook with a FireGL 7800 GFX card and tried some HowTo's to install either XGL or AIGLX. Both ended up having no DRI when loading XGL/AIGLX. But I do get DRI instantly after clean installing dapper on my machine (radeon driver), so I guess it would be technically possible! The problem is that my FireGL is only supported by the 'radeon' driver. So, is there a way to get XGL/AIGLX working on this hardware?

Hope some people can help!

eClaW

---

### Post by eClaW on 2006-11-01
Ok, I figured it out using [this]("https://help.ubuntu.com/community/RadeonDriver") and [this guide]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX"). Actually no big deal, really. If you have a card of this generation you should change DefaultDepth from 24 to 16 in /etc/X11/xorg.conf, though, otherwise it will be pretty choppy and fps from 30 to 60. With DefaultDepth set to 16 you get 60+ almost constantly. Very cool!

Had some problems with playing movies but they vanished after using the console (!) version of mplayer. Best thing around for this kinda stuff!

---

