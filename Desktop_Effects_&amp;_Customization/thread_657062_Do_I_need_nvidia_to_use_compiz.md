---
title: "Do I need nvidia to use compiz?"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by agim on 2008-01-03
I am curious to know what I would need to start using compiz. Do I need a special graphics card? I can't really seem to find this info anywhere else and I hope someone here can point me in the right direction.

---

### Post by chewearn on 2008-01-03
You need a graphics card that support 3D.  I personally have successfully used compiz with nvidia and intel graphics.  Of course, ati works too.

---

### Post by FuturePilot on 2008-01-03
You don't necessarily need a Nvidia card. Compiz should run fine on most higher end Intel cards and some ATI cards, although you might need XGL for that. Nvidia seems to work the best though. No need for XGL or anything like that.

---

### Post by diwas on 2008-01-03
I have a 64MB graphics card...will it be able to support Compiz and Emerald? By the way it is integrated graphics card. 
Thank you.

---

### Post by xeth_delta on 2008-01-03
> **diwas said:**
> I have a 64MB graphics card...will it be able to support Compiz and Emerald? By the way it is integrated graphics card. 
Thank you.

What card is it? I have got it working on two integrated cards, an Intel 945GM and an ATi Radeon Mobility 9000 IGP. Some of the more demanding effects will be a tad slower when you have a lot of windows open. Performance is nevertheless good, or above acceptable in the case of that old Radeon graphics card I mentioned. The water effect (and perhaps a couple more) which require shaders might not be available, if I am not mistaken.

Xeth

---

### Post by diwas on 2008-01-03
Yes, the water effect was not available. My motherboard id is D845GVSR, pretty old...but its cool. By the way, wat is water effect and does compiz has that UI like vista, ie when a user presses Alt+Tab the current window are stacked 1 by 1...

---

### Post by xeth_delta on 2008-01-03
> **diwas said:**
> Yes, the water effect was not available. My motherboard id is D845GVSR, pretty old...but its cool. By the way, wat is water effect and does compiz has that UI like vista, ie when a user presses Alt+Tab the current window are stacked 1 by 1...

Compiz offers much more than that, give it a run and you will be able to see :) I don't think the windows stack effect is really that useful, at least not to me, but something similar is included in the latest versions of compiz.

---

### Post by anyo409 on 2008-01-03
you can go with Nvidia card ....... I have used few of them & compiz really runs smooth. I use 7600.

---

### Post by psyopper on 2008-01-03
Compiz works with almost any per-pixel shading 3D accelerator; some work better than others. For instance, the Intel 8xx series are blacklisted because they aren't capable of performing ALL of the features (like video playback). You can remove them from the blacklist and use them but they won't work nearly as well.

Generally speaking any Nvidia GeForce chipset (from 4xx and up), any ATI chipest based on the R400 and up and any Intel chipset based on the 9xx and up will work. 

None of the S3 or VIA chipsets will work. At least not that I've seen.

---

### Post by agim on 2008-01-03
Very noobish question. How do I find out what graphics card I have?

---

### Post by xeth_delta on 2008-01-03
> **agim said:**
> Very noobish question. How do I find out what graphics card I have?

Open a terminal, you can use one of the following:
```
lspci | grep -i VGA
lshw -C video
```

To find out whether your system uses hardware 3D acceleration: 
```
glxinfo | grep -i direct
```

There must be some graphical inerfaces that will let you know this information, but I am not sure what what they should be for Gnome, as I am a KDE user.

---

### Post by Seisen on 2008-01-03
> **agim said:**
> Very noobish question. How do I find out what graphics card I have?

Type in ```
lspci
``` in the terminal.

---

### Post by agim on 2008-01-03
As of two days ago I am a KDE user too!. The interface is unbelievable. I actually know some C++, and I am going to go out and buy a QT book asap. I love it.

As far as the graphics card goes...

lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

and

glxinfo | grep -i direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect


I want to know if it is possible to run 3D graphics with this card, or what. And where to I set LIBGL_DEBUG to verbose?

I found something that looked promising on this page
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_R61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_R61).
I will try this and report back.

Thanks for the great responses.

---

### Post by r41nz0r on 2008-01-03
I would advise you to buy an nVidia gfx card if you are interested in getting one.

---

