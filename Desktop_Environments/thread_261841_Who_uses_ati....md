---
title: "Who uses ati...?"
date: 2006-09-20
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-09-20
Do you people notice any problems with the drivers such as system hanging/screen going black or white when you log off, shut down, or restart. Also do you ever get jaggy frame rate that runs smooth but chokes every 3 seconds in a continuing pattern? Jw since Im getting these problems and I dont see many people reporting such problems. Then again seems like the majority of linux users use nvidia :rolleyes:

---

### Post by roachk71 on 2006-09-21
What card are you using (eg. mine is an integrated IGP340M)?

I have a code snippet you could enter into your /etc/X11/xorg.conf file (as root), if you're not using one of the newer cards:

```
Section "Device"
    Identifier    "your card here" (don't change this or the line after the next)
    Driver        "radeon"
    BusID        "PCI:1:5:0"
    Option        "AGPMode"        "4"
    Option        "AccelMethod"        "EXA"
    Option        "RenderAccel"        "true"
    Option        "EnablePageFlip"    "true"
    Option        "DDCMode"
    Option        "SubPixelOrder"        "NONE"
    Option        "ColorTiling"        "false"
EndSection
```The block of Options above works on the majority of these cards, except the latest and greatest (which require a proprietary driver available from ATi.)

And the Radeon designation uses the Radeon driver instead of the standard ATi one (does this really make a difference? Does on mine!) :cool:

---

### Post by randell6564 on 2006-09-21
I use an ATI radoen, and it seems to work fine.  The only problem with it is that I want to be able to install and use compiz. (I like that see through look for open windows!), but I have been told that Compiz does not work good, or at all, with ATI.

---

### Post by WalmartSniperLX on 2006-09-21
> **roachk71 said:**
> What card are you using (eg. mine is an integrated IGP340M)?

I have a code snippet you could enter into your /etc/X11/xorg.conf file (as root), if you're not using one of the newer cards:

```
Section "Device"
    Identifier    "your card here" (don't change this or the line after the next)
    Driver        "radeon"
    BusID        "PCI:1:5:0"
    Option        "AGPMode"        "4"
    Option        "AccelMethod"        "EXA"
    Option        "RenderAccel"        "true"
    Option        "EnablePageFlip"    "true"
    Option        "DDCMode"
    Option        "SubPixelOrder"        "NONE"
    Option        "ColorTiling"        "false"
EndSection
```The block of Options above works on the majority of these cards, except the latest and greatest (which require a proprietary driver available from ATi.)

And the Radeon designation uses the Radeon driver instead of the standard ATi one (does this really make a difference? Does on mine!) :cool:

Im using a x1600pro, so I dont know if you consider it old or new lol Its in part of the x1k series, their latest, but they have newer cards now. :D

---

### Post by Anduu on 2006-09-21
> **WalmartSniperLX said:**
> Do you people notice any problems with the drivers such as system hanging/screen going black or white when you log off, shut down, or restart. Also do you ever get jaggy frame rate that runs smooth but chokes every 3 seconds in a continuing pattern? Jw since Im getting these problems and I dont see many people reporting such problems. Then again seems like the majority of linux users use nvidia :rolleyes:

The only issue i have with my ATI Radeon 9600 is the white screen on logout sometimes which a ctrl+alt+backspace takes care of.

> **randell6564 said:**
> I use an ATI radoen, and it seems to work fine.  The only problem with it is that I want to be able to install and use compiz. (I like that see through look for open windows!), but I have been told that Compiz does not work good, or at all, with ATI.

Whoever told you that is dead wrong...I run XGL/Compiz fine on my ATI.

---

### Post by randell6564 on 2006-09-21
> **Anduu said:**
> 
Whoever told you that is dead wrong...I run XGL/Compiz fine on my ATI.

GREAT!  can ya point me to a tutorial for installing and using it then?

---

### Post by Anduu on 2006-09-21
Here is the one I used:
[http://compiz.net/viewtopic.php?id=389](http://compiz.net/viewtopic.php?id=389)

Good luck :)

---

### Post by randell6564 on 2006-09-21
> **Anduu said:**
> Here is the one I used:
[http://compiz.net/viewtopic.php?id=389](http://compiz.net/viewtopic.php?id=389)

Good luck :)

Thanks my friend!

---

### Post by Melcar on 2006-09-21
Compiz runs great on my 200M.  Only problem is the screen corruption on certain situations (logout, login, etc).  I use this guide to get it to work
[https://help.ubuntu.com/community/CompositeManager/](https://help.ubuntu.com/community/CompositeManager/)

---

### Post by Monstroxus on 2006-09-21
I also use ATI, no problems here, when playing Warsow (kind of Unreal), wow! so smooth and fast, no hickups or whatsoever. If I remember well, EasyUbuntu will install ATI drivers automatically. Maybe you can try that. (not sure, since I'm a newbie)

---

