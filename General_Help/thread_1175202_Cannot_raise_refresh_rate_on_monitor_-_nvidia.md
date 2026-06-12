---
title: "Cannot raise refresh rate on monitor - nvidia"
date: 2009-05-31
forum: General Help
---

### Post by mirnander on 2009-05-31
Hello all - 

I'm new to Ubuntu - and I'm loving it - despite the trouble I have had getting various things working, like sound, my aiptek tablet, etc, I find the everything else about the design of Ubuntu to be a delight to work with.

At any rate, here's the first trouble I've run into that I absolutely can not figure out how to fix on my own. 

I have the Nvidia driver installed, and it pulls up the Nvidia x server settings just fine, but nvidia panel does not offer me settings to improve the refresh rate or screen resoution on my monitor. The highest res offered is 1024x768 at a refresh rate of 60Hz. I have an envision en910e monitor, which should display at 1600 x 1200 85Hz. When I tried plugging in my old (and smaller) sony trinitron all the settings were correct. I'm guessing that's because the trinitron is/was a more popular product.

I've tried following the Ubuntu documentation on editing xorg.conf file to no avail. I don't know where to find the information I need for my monitor and I don't really understand the xorg.conf file itself (though I did manage to figure out how to open up the nautilus, locate the and edit the file, temporarily mess up my system, and then save the system. :0 

So before I go mucking things up again, could someone please help me with some very explicit (ie dumbed down,) instructions on how to go about getting the proper settings out of my monitor. As of now I feel like I am looking at it through a box fan.


Thank you :)



PS - also, does anyone know why the sound broke after upgrading to KDE/kubuntu or how to fix it? I'm happy enough with gnome, but I would like to experiment more with KDE.

---

### Post by CatKiller on 2009-06-01
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

According to the Windows "monitor driver" that I found on [this page]("http://envisiondisplay.com/products.asp?EPage=products&SMenu=en910e") the values you're looking for are

```
        HorizSync       30-95
        VertRefresh     50-160

```

---

### Post by Dr Small on 2009-06-01
Open a terminal and type:
```
nvidia-settings
```

---

### Post by mirnander on 2009-06-01
CatKiller - Thank you so much! Wonderful - and easy enough for a noob like me to follow :) Cheers.

I hope you don't actually kill cats 
Dig the quote

---

