---
title: "i can only get 800x600"
date: 2009-05-04
forum: General Help
---

### Post by xoger on 2009-05-04
hi i resently installed ubuntu 9.04 on my mums computer and can only get 800x600 resolution.
if i install the nvidia driver i can only get 640x480.
my graphics card is a geforce 3 ti 200.
any help would be most appreciated 
thanks in advance

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

### Post by garethclark on 2009-05-04
You might want to try setting the screen. I had a similar problem when updating to 8.10. After spending hours with the graphics card i discovered that it was to screen that was not recognized.

Type the following in the terminal:

sudo displayconfig-gtk


Then under screen - model. Select Generic and the screen resolution you require. Then make sure the resolution is also checked to what you want. Then it should work.

---

### Post by CatKiller on 2009-05-04
displayconfig-gtk isn't in 9.04. It was taken out after Hardy because it didn't work with the newer versions of X, and only Ubuntu was using it. I understand that it's being re-implemented for future versions, using KDE's guidance.

---

