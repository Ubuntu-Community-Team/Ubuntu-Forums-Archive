---
title: "Can't Get BERYL to install on ATI X600"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by OxideNOS on 2007-05-12
I have ATI Radeon X600 graphic card and this is my first time install Ubuntu feisty fawn.  I can't seem to get Beryl installed.

I initially installed ATI drivers using ENVY and they installed fine but now i can't get to install beryl. I used all guides on this website but still does NOT work.

Any suggestions?  Am i getting problems because i installed my ATI drivers through ENVY. Also i don't see any xorg.conf on etc/x11/ after installing ATI drivers using ENVy.

---

### Post by OxideNOS on 2007-05-12
the only files is see in /etc/x11/ folders are xorg.conf.fglrx- 0 , xorg.conf.original- 0 and xorg.conf_backup_  . I think these are created and modified by EVNY. so thats is all the info i have .. how can i install beryl ??

---

### Post by strumluff on 2007-05-12
Great so you have the drivers set up. Now for this ATI card I don't know if the X600 is fully supported with the open-source drivers but as you installed with Envy I would think it installed the fglrx drivers.

You now need to install XGL and create an XGL session to run Beryl.

Follow this guide, it's rather long but has everything you need to install Beryl with XGL: 

[Linky]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

---

### Post by Znupi on 2007-05-12
I used this [linky](https://help.ubuntu.com/community/Beryl/ATI/Feisty) to help me install beryl, on an X550 card, so it's not too far away... Didn't use ENVY though...

---

### Post by strumluff on 2007-05-13
> **Znupi said:**
> I used this [linky](https://help.ubuntu.com/community/Beryl/ATI/Feisty) to help me install beryl, on an X550 card, so it's not too far away... Didn't use ENVY though...

Yeah that guide is basically the same thing apart from you just have to remember that you've pinned all beryl files in your apt/preferences for when a beryl update that works is released. 

It doesn't matter which method you choose to install the graphics drivers. The simplest method is to install the graphics drivers from the Restricted Drivers Manager, I would use Envy as a second choice.

---

