---
title: "Screen Resolution question"
date: 2009-05-06
forum: General Help
---

### Post by Furm on 2009-05-06
Hey guys, my name is Josh and I'm new to Ubuntu. I just reformatted from XP to 9.04 this evening. I'm loving it very much so far. Lots of new interesting things to learn. One question I is about the screen resolution. I'm used to having 1680x1050/1600x1200, but I've found that those resolutions are not available options. I've been trying a few commandlines and also tryed to run a ATI Linux driver for my videocard, however i wasn't successful in the install. I was wondering if there is a proper technique to opening up the screen resolution that you guys might be able to share with me.

Thanks!

---

### Post by 4Orbs on 2009-05-06
Once you get the driver installed for your ATI card, those resolutions you want will probably become available. The driver is important to your happiness.

---

### Post by Furm on 2009-05-06
any leads on a driver for a Radeon 9700. The one i got off of the ATI website was version 9.3 x86     It is a .run file   I tried to get it going through the commandline. Is there any other way to open a .run file properly?

Thanks again

---

### Post by 4Orbs on 2009-05-06
I don't know about your particular card and driver (I'm an nVidia user). Did you check in you system Hardware Drivers Mgr for the driver? If Ubuntu has an available driver for your card, that would be the easiest and safest way to get it installed.

---

### Post by netwarriorwy on 2009-05-06
Hi Furm!

First try to check the resolutions you have available at

> System->Preferences->Display

Then go to 

> system->Administration->Hardware Drivers

The system should check for any third-parties drivers you may need. I have an [COLOR="DarkSlateBlue"]Nvidia Geforce 8600 GT[/COLOR] on my desktop and the Ubuntus Hardware Driver option looked for the driver i needed.

I hope that helps :)

---

### Post by Furm on 2009-05-06
still nothing :( and my highest resolution on the display settings are

1280x1024 5:4
1280x960 4:3

what kind of resolution can you guys get just out of curiosity

---

### Post by CatKiller on 2009-05-06
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

