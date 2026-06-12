---
title: "Nvidia driver problems"
date: 2006-06-10
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-10
Hi,

Last time I tried Ubutnu (5.04 or whatever it was), I had problems with the nvidia drivers and now it seems that I've a similar problem.

After installing 6.06, the first thing I did was to follow the wiki on installing nvidia drivers. I did..and I got an Nvidia logo on bootup but I couldn't set a screen resolution of more than 1024x768....the same res offered with no Nvidia driver. What I did get with the driver was a max refresh of 85Hz...

Anyway, I tried out Easyubuntu (to install some other stuff) as this installed Nvidia drivers...which I though might cure my screen res problem. It didn't. In fact, after using that, I don't get an Nvidia logo anymore and am back to 60Hz max refresh.

So, I 'uninstalled' the Nvidia drivers using the package manager then reinstalled them. I'm now in the same position as with 5.04 in that the Nvidia drivers don't appear to install properly. i.e. It says they have been installed...but no logo...crap screen res and 60Hz refresh.

Is there a way to get these drivers back on and working + get myself a screen resolution better than 1024x768? 

Also, I have a GeForce 4 Ti4200....Should I be using the glx or legacy drivers? I was using the Glx and I don't consider the GF4 to be an 'old' GF.

This really was one of the most frustrating things about Ubuntu and the main reason why I reverted back to using Slax...

Ta,
Xeno

---

### Post by tseliot on 2006-06-10
Read this guide of mine (and its problems section) and you will find everything you need:
[http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia]("http://www.ubuntuforums.org/showthread.php?t=139264&highlight=nvidia")

---

### Post by xenomorph99 on 2006-06-10
Thanks! That has at least got me back to having a refresh of 85Hz but I still get no option in the 'system->pref->screen resolution' applet of > 1024x768 res.

Do I have to hand mod the xorg.conf file or something?

Ta,
Xeno

---

### Post by B_Stil on 2006-06-10
I'm going to assume you have a 17" or larger monitor?

---

### Post by xenomorph99 on 2006-06-10
19'' Fujitsu-Siemens monitor.

I just hand modded the xorg.conf by adding a "1280x1024" item to the start of each screen res 'list' and I now have just that setting...at 85Hz..which is good except that I do have a bit of 'graphic corruption' around the clock on the top panel bar (if transparency is enabled).

Why is it not 'autodetected' ? After all, you might expect a Gf4 card to want to run a res > 1024x768.

Thanks again,
xeno

---

### Post by tseliot on 2006-06-10
Read point 5 of the Problems Section.

If that doesn't solve your problem you can try point 10 of the Problems Section.

---

### Post by tseliot on 2006-06-10
[QUOTE=xenomorph99]Why is it not 'autodetected' ? After all, you might expect a Gf4 card to want to run a res > 1024x768[/QUOTE]
I didn't write the code of the Xserver (and I would never be able to do that) and I have no idea of the reason of its behaviour with your card.

---

