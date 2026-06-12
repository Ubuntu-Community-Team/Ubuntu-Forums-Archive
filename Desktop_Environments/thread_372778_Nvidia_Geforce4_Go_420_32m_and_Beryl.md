---
title: "Nvidia Geforce4 Go 420 32m and Beryl"
date: 2007-02-28
forum: Desktop Environments
---

### Post by Preheated Bibby on 2007-02-28
Hey guys. I was wondering if anyone could help me with this. After numerous times (and re installations), I still have not been able to get Beryl running on my laptop. I think the problem maybe my video card (listed in title) but I'm not 100% sure.  When trying to run beryl from terminal, this is what I get..```


**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Xlib:  extension "GLX" missing on display ":0.0".
Root visual is not a GL visual
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

So I think I'm really close because of AIGLX running, but I'm not sure. Any suggestions are appreciated, thanks in advance guys!

---

### Post by Dr. Nick on 2007-03-01
Have you installed the nvidia-glx drivers yet?

---

### Post by bimmerd00d on 2007-03-01
I could not for the life of me ever get Beryl to run well with teh 16mb version of this card on my Toshiba 6100.  3d acceleration was enabled, tuxracer ran in 800x600 with zero problems, but it just couldn't handle Beryl.  Here are my xorg.conf and options settings that worked with the nvidia-glx driver in the repos.

[http://bimmerd00d.com/linuxbak/tosh6100/](http://bimmerd00d.com/linuxbak/tosh6100/)

---

### Post by M4LFUNCT10N on 2007-03-02
> **bimmerd00d said:**
> I could not for the life of me ever get Beryl to run well with teh 16mb version of this card on my Toshiba 6100.  3d acceleration was enabled, tuxracer ran in 800x600 with zero problems, but it just couldn't handle Beryl.  Here are my xorg.conf and options settings that worked with the nvidia-glx driver in the repos.

[http://bimmerd00d.com/linuxbak/tosh6100/](http://bimmerd00d.com/linuxbak/tosh6100/)

You need to run it with XGL and the older stable video drivers from Nvidia, version 8774.

I'm running Beryl with the 16MB 420 in my Satellite 1415-S173

---

### Post by Mimou on 2007-03-02
Hi!

I succeded to launch Beryl on a Geforce 4MX 440.
I see you use AIGLX, but on Edgy (if I don't do mistake) xorg contains (AIGLX/XGL).
And if you use NVidia drivers you don't need AIGLX.

So try with xorg (7.1.xx).

For my install, I used the NVidia script, to install the latest version, I used xserver-xorg-dev. And everything is OK.
But I can't run all effects (I disable the opening/closing effects :D ).

Good Luck :)

---

### Post by Dr. Nick on 2007-03-02
You will also be unable to use the water effect and a few others that require pixel shaders

---

### Post by Preheated Bibby on 2007-03-04
Well lets see if I can start chipping away at this. For the Nvidia drivers, I used a easy install called envy? I believe. It was on digg a few weeks ago, and thats how I learned about it. So I used that, so I'm not 100% sure on what my drivers actually are. I am running 6.10, so I don't need AIGLX ?  


> So try with xorg (7.1.xx).

Try with? Is there a place I can download this?? Sorry for being such a newbie, and thanks for all the help guys!

---

### Post by TheD0ct0r on 2007-03-04
Hi, i'm new to these forums. I'm trying to install Ubuntu on my computer but i don't think the video card s right, it'll get up to a certain point then the screen will go black and stay like that. I have an Intel(R) 82810E Graphics Controller (Microsoft Corporation). Go easy on me if i'm being thick, i'm only 14

---

### Post by packjamNL on 2007-07-04
So does beryl run on the Toshiba 6100 now?
I got a Feisty Fawn copy here, now I'm trying FC 7 to get beryl running.

---

