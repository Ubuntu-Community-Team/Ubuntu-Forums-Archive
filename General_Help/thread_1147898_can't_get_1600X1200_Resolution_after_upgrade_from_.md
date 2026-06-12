---
title: "can't get 1600X1200 Resolution after upgrade from 8.10 to 9.04"
date: 2009-05-03
forum: General Help
---

### Post by Hyper Tails on 2009-05-03
hi i run Vista and jaunty and I built a pc and I have an ati readon hd 3600 and I installed my graphics card driver correctly and I cannot get my resolution to be 1600X1200.

I could back on hardy and intrepid by why not in jaunty?

help will be thanked as usual

---

### Post by CatKiller on 2009-05-04
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

### Post by Hyper Tails on 2009-05-05
how do i do that in gedit?

I already know how to open the file in gedit

monitor: acer 19 ince lcd

---

### Post by Hyper Tails on 2009-05-06
................................

---

### Post by Hyper Tails on 2009-05-07
.....................Help?

---

### Post by CatKiller on 2009-05-08
So have you put those lines in your xorg.conf?

---

### Post by Hyper Tails on 2009-05-08
yes

---

### Post by Hyper Tails on 2009-05-10
......................................

---

### Post by Yellow Pasque on 2009-05-10
Pastebin your /var/log/Xorg.0.log
[http://ubuntu.pastebin.com/](http://ubuntu.pastebin.com/)

---

