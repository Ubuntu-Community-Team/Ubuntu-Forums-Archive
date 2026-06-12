---
title: "Multi Monitors settings are lost after restart (kubuntu 10.04)"
date: 2010-05-04
forum: Desktop Environments
---

### Post by pompos on 2010-05-04
Hej,

fortunately, it is possible to use the KDE settings to set up multiple monitors since kubuntu 10.04. However, I have to set it up every time I start my computer. This getting quite annoying as I have to change the monitors settings three times to get the desired result.
So... how can I convince KDE to save the settings and use them also after a restart?

---

### Post by [buri] on 2010-05-09
hi, I have the same problem. When I restart the computer all the settings(for the display) are lost.

---

### Post by pixel_pusher on 2010-07-30
Same problem here, except that I lose the settings after each logout. I use a laptop with an external monitor plugged in via vga. Kubuntu was installed thru synaptic (regular Ubuntu 10.04 install). 

One quirk is that if I dont use the other monitor, my display settings are fine, and get loaded every time. But, as soon as I'm plugged into the external monitor, both monitors default to 1024x768 and the external is treated as the main monitor, while the laptop screen is set as a clone of the external.

If the OP is still reading this, did you install in the same way (installing kubuntu-desktop from synaptic), or did you install kubuntu from the get-go? I'm wondering if doing it fresh would maybe solve the issue for me.

---

### Post by sponsoredbythewind on 2010-08-14
I have the same problem with Kubuntu/KDE4.5. 
The configuration is saved with Gnome, but doesn't work with KDE.
See [http://ohioloco.ubuntuforums.org/showthread.php?p=9711731](http://ohioloco.ubuntuforums.org/showthread.php?p=9711731) for a hack.
See man xrandr for the syntax.

---

### Post by cblanquer on 2010-09-10
Identical problem:
[LIST]
[*]main screen 1680x1050
[*]aux screen 1280x1024
[/LIST]
Set as a single screen.

On reboot (I did not try logout) it falls to clone screen with 1280x1024.

I have tried AMD-ATI drivers and that works well BUT compiz gets deactivated and the screen is not well processed.

Worst, I have another Kubuntu PC which works properly with 2 screens, but I cannot find out what I did to fix it. :-( :-(
To be investigated.

---

### Post by mister_playboy on 2010-09-10
I have the same problem... very annoying to have to apply the setting three times at every boot. :mad:

I also run into quite a bit of trouble switching between my TV and my laptop.  All too often, something goes wrong during the screen switch and I end up with blank screens on both monitors... in that case all I can do is CRTL+ALT+DEL to logout and login back in again. #-o

---

### Post by datacrusher on 2010-10-14
Same problem here. Usung kubuntu (kxstudio 10.04).

Have two monitors with same resolution 1990x400 and I have to every boot go to settings and tell that the second monitor is not a clone, and its on the left of .. etc .etc..

very annoying. It it could just have "save settings" options would be fine.

---

### Post by datacrusher on 2010-10-14
Is there a way to export the current / working screen configuration to a xorg.conf file, so it could be persistent?

---

### Post by psynautic on 2010-10-15
I added this:
```
xrandr --output DVI-1 --auto --right-of DVI-0
```

to: /etc/kde4/kdm/Xsetup

as I read [here]("http://kubuntuforums.net/forums/index.php?topic=3113408.0")

psynautic.

---

### Post by foggytown on 2010-11-08
Thanks psynautic!  You saved me a ton of grief.  I had placed my xrandr script in ~/.kde/start which caused it to load late in the process.  This forced me to rearrange panels and plasmoids at every boot.

This issue is a known KDE bug, introduced in 4.4 and fixed in the 4.6 branch...which we won't see for quite some time.

---

