---
title: "Xorg 6.8 and X config File"
date: 2006-06-07
forum: Desktop Environments
---

### Post by w1z4rd on 2006-06-07
Xorg 6.8 and X config File

Trying to sex my desktop up somewhat, and been a n00b, I have broken it a couple of times, and when I break it, it normally means a reinstall as I do not yet have the technical know-how to repair things .....yet.

I have tried to enable translucency and shadows on my windows, and I just restarted X, and got this error:

> 
Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

Now... lol, um... wheres the config file, and what may be the best way to install Xorg 6.8

FYI: Im running Kubuntu 6.06 LTS Dapper Drake, and have a NVidia PCI Express 256mb gfx card.

Thanks in advance.

---

### Post by UbuntuJohan on 2006-06-07
As far as I can see from 
[http://packages.ubuntu.com/dapper/allpackages](http://packages.ubuntu.com/dapper/allpackages)
The XORG version in dapper is 7.0.0 but I don't have a machine available to confirm that.

The configuration file is called xorg.conf
and is located in /etc/X11/

//Johan

---

### Post by arizonagroovejet on 2006-06-07
[QUOTE=UbuntuJohan]As far as I can see from 
[http://packages.ubuntu.com/dapper/allpackages](http://packages.ubuntu.com/dapper/allpackages)
The XORG version in dapper is 7.0.0 but I don't have a machine available to confirm that.
[/QUOTE]

You are correct. Dapper ships with xorg 7.0.

---

### Post by w1z4rd on 2006-06-07
I enabled the option to give my windows transparancy and shadows succesfully (thanks guys!), but until I disabled the option KDE ran dead slow :( Everything was laggy, and it felt terrible.

I dont think I dont have the hardware to run it, cause I am running over 2GB of RAM, have a newish 256mb PCI express Nvidia, 400GB in sata disk space, Intel p4 3Ghz chip with hyperthreading.

Is this how it currently functions at the moment? Does it prehaps need super hardware.. .or the most llikely scenario... am I doing something wrong? :) lol

I know when I enabled it, it mentioned something about been in a beta stage, so prehaps that has something to do with it..

---

### Post by w1z4rd on 2006-06-08
Okay, sorted out the problem I was having with tranlucency and shadows with windows.

In you xorg.conf file in /etc/X11/

Change:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

```

to

```

Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

```

Worked for me, now my windows are not laggy at all, and I have to admit, the effects are pretty leet.

---

