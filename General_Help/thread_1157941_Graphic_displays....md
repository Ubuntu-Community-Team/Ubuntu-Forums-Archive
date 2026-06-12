---
title: "Graphic displays..."
date: 2009-05-13
forum: General Help
---

### Post by zilu54 on 2009-05-13
First of all...its my very first time in ubuntu so after I transfer to ubuntu from windows, the one thing after i formated my pc I cannot change my screen resolution from 800 x 600 to 1024 x 768.

I already try from researching and terminals and blah blah blah...but I still dont get it.

can you guys help me?

> Mini Specs.
Ubuntu 9.04
Intel Processor and a motherboard built-in video/graphic card.

---

### Post by bolter40k on 2009-05-13
i can try to help but i will need to know what motherboard you have

---

### Post by zilu54 on 2009-05-14
> **bolter40k said:**
> i can try to help but i will need to know what motherboard you have
I  have an ECS ELITEGROUP motherboard, and its built-in video card.

---

### Post by CatKiller on 2009-05-14
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

