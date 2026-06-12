---
title: "LInux distros that support NVIDIA GeForce 9500 GS"
date: 2009-02-09
forum: General Help
---

### Post by Couto on 2009-02-09
Do you know ANY Linux distros that support NVIDIA GeForce 9500 GS card?

Ubuntu 8.1 doesn't support it meaning I can't use Compiz and stuff, which really sucks.

If anyone has this card and has Compiz and that stuff working I'd love help.

---

### Post by photon_man62 on 2009-02-09
Advice: buy a new graphics card. :)

Sorry but the 9500 GS is only supported on Windows. I have yet to find a driver for it on Linux :D

I was surprised that THIS laptop's graphics card was supported (8600M GS), since I even had trouble with drivers on WINDOWS.

But it's working fine on Linux. If yours doesn't work then you can always try downgrading Ubuntu to 8.04 and enabling a driver there, might work for you :)

---

### Post by bettlebrox on 2009-02-10
It doesn't work with the NVidia drivers?

Nvidia's page say that the 9500M GS and the 9500 GT are both supported:
[http://www.nvidia.com/object/IO_18897.html]("http://www.nvidia.com/object/IO_18897.html")

Updated: I just checked Nvidia's page and they don't list the 9500GS as supported under Linux:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)
That's a real pain, and a surprise, I thought NVidia support Linux on all their GPUs?

Another option is to try the open source "nv" driver. This might get you higher resolutions, but poor 3D support.

---

### Post by Couto on 2009-02-10
My resolution is max @ 1680x1050 without the driver even, it'd just be cool for a little extra 2D support simple dragging non-laggyness stuff would be cool to run some things like Compiz, play some games like America's Army. I'll live though, thanks guys.

---

### Post by Couto on 2009-02-10
@ the 8.04 comment I cannot get internet on 8.04 lol, I know it's weird.

---

### Post by Couto on 2009-02-10
So, nobody knows any distros?

---

### Post by jespdj on 2009-02-10
If there is no nVidia driver for Linux that supports that video card, then there is no Linux distro on which the card will work.

Is the 9500 GS a very new model? You'll just have to be patient until nVidia releases a new driver version which supports the 9500 GS.

The latest version of the nVidia Linux driver at the moment is [version 180.29](http://www.nvnews.net/vbulletin/showthread.php?p=1927376). But unfortunately, the 9500 GS is not in the [list of supported GPUs](ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/appendix-a.html). Which is a bit strange - the 9500 GT and also the 9500M GS are, but not the 9500 GS... :(

---

### Post by LowSky on 2009-02-10
most liekly in 6 months time the card will be supported. You can blame Nvidia for not releasing the drivers.

so if you want a Distro that will run 3D then I suggest Windows....lol

---

### Post by Couto on 2009-02-10
> **jespdj said:**
> If there is no nVidia driver for Linux that supports that video card, then there is no Linux distro on which the card will work.

Is the 9500 GS a very new model? You'll just have to be patient until nVidia releases a new driver version which supports the 9500 GS.

The latest version of the nVidia Linux driver at the moment is [version 180.29](http://www.nvnews.net/vbulletin/showthread.php?p=1927376). But unfortunately, the 9500 GS is not in the [list of supported GPUs](ftp://download.nvidia.com/XFree86/Linux-x86/180.29/README/appendix-a.html). Which is a bit strange - the 9500 GT and also the 9500M GS are, but not the 9500 GS... :(

9500 GS is in the 177 release but it's not working with Ubuntu so idk wtf is wrong. It's new but it's not old you know

---

### Post by bodhi.zazen on 2009-02-10
> **Couto said:**
> Do you know ANY Linux distros that support NVIDIA GeForce 9500 GS card?

Ubuntu 8.1 doesn't support it meaning I can't use Compiz and stuff, which really sucks.

If anyone has this card and has Compiz and that stuff working I'd love help.

Nvidia has not open sourced their drivers, thus the drivers are closed source and supported directly by nvidia, not linux or the open source community.

As has been suggested in this thread, I suggest you post on the nvidia forums and ask them directly about linux support for your card.

---

### Post by zuchini on 2009-04-19
I have one in a newer hp desktop and all 3d effects including cube, min/max effects, yada yada yada work just the way they're supposed to. I'm currently running the 9.04 ubu beta, before that i ran 8.10 ubu and kubu, and ive also played around with sabayon 4. All handled 3d effects just fine. Also I have two 22" acer monitors hooked up to that one 9500gs both running a res of 1680x1050 each... No probs... Cube looks neat-o on dual monitors too. I think the 9500 gs is a decent lower midrange card. Its nothing super duper awesome but it works well enough. Its horrid for really demanding games though but that's the only downside i've found with this card. If your having problems with one i dont know why.

Also, future reference... I haven't noticed anything with mine but it seems alot of people gripe about a fan noise from this card after a few months of use.

Edit: it does have fan problems... and they are LOUD...

---

### Post by toffuuu on 2010-05-22
Is there any new info on this?  cause i did find this [ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/README](ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/README)   now I am not using Ubuntu as of yet cause I don't have the PC yet that does have the geforce 9500 GS card,   but I most likely will only if I'm very sure this card is supported...    so please  confirm any info on this?   Thanks..

---

### Post by bodhi.zazen on 2010-05-22
> **toffuuu said:**
> Is there any new info on this?  cause i did find this [ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/README](ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/README)   now I am not using Ubuntu as of yet cause I don't have the PC yet that does have the geforce 9500 GS card,   but I most likely will only if I'm very sure this card is supported...    so please  confirm any info on this?   Thanks..

This thread is more then a year old.

If you wish to know the status of the nvidia drivers I suggest the nvidia forums:

[http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14)

Over the last year , there has been an opensource driver developed, Nouveau and gallium

[https://fedoraproject.org/wiki/Test_Day:2010-04-13_Nouveau](https://fedoraproject.org/wiki/Test_Day:2010-04-13_Nouveau)

[http://www.phoronix.com/vr.php?view=14591](http://www.phoronix.com/vr.php?view=14591)

These drivers are in testing and development in both Fedora and Ubuntu

---

