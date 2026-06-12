---
title: "Support for my wireless card *tear*"
date: 2005-04-04
forum: Desktop Environments
---

### Post by waxle on 2005-04-04
I use a D-Link DWL-650 pcmia adapter on my dual-boot Dell laptop. This model is not supported automatically, so I tried to manually edit my \filesystem\etc\pcmia\config.opts file as per [http://tuxmobil.org/pcmcia_ci10092.html](http://tuxmobil.org/pcmcia_ci10092.html). This does not work even when I use 
sudo gedit filename
because gedit does not seem to support nested files. This is extremely aggravating, as I need to use this card to acess the internet to update (i acess the forum through windows, god forbid). The whole reason I installed Ubuntu in the first place was due to the higher security. Help me! Please!

---

### Post by lao_V on 2005-04-05
you need to type in **sudo gedit /etc/pcmcia/conf**

---

