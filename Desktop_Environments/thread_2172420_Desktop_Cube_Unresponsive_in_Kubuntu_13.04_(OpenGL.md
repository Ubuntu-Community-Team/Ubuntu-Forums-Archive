---
title: "Desktop Cube Unresponsive in Kubuntu 13.04? (OpenGL)"
date: 2013-09-04
forum: Desktop Environments
---

### Post by BlacklightHalo on 2013-09-04
I've just started using KDE with this computer. When I first installed it, before my reboot, the version of Desktop Cube in the Desktop Effects menu was working perfectly and looking great. Then there was some funny business with my login credentials, which I figured out was my error (I assumed my username was one thing when it was another.) So now I'm logged back in to KDE, but for some reason, I'm being told that "21 effects could not be loaded," and under details I see "Desktop Effect system is not running." I have "enable desktop effects at startup" checked and it was working fine before. It seems to me that if it were a matter of my graphics card being inadequate or something, it wouldn't have made it work in the first place. Am I wrong about that? o.O

Looking around, it seems like the "Compositing Type" under "Advanced" in "Desktop Effects" is especially pertinent. I tried switching to OpenGl and the Raster Qt, but got this error message after a whole lot of twitching and flickering from kWin:

[ATTACH=CONFIG]246019[/ATTACH]

This seems to be the problem - the cube won't work without OpenGL, and OpenGL doesn't seem to want to "take hold" somehow. Does anyone have any ideas as to how to get my oh-so-lovely cube working again?

---

### Post by nut-kicker on 2013-09-06
It seems I have the exact same problem, and after some experimenting, *every Ubuntu-based distro I've tried has the problem* (Netrunner, Kubuntu and Mint KDE). Weirdly, it's **only** Ubuntu-based distros that do this (Fedora, Kororra and Rosa work perfectly). It's not the graphics card nor the drivers either because I tried on two vastly different computers and got the same results (First an I7 with a GTX and then an FX with a Radeon). OpenGL just *does not* want to work. Something from the Ubuntu core is fvcking things up for everyone. No, I don't know what; I'm just an average user.

---

### Post by nut-kicker on 2013-09-06
Ok, so I tried to follow the instructions in this thread on compiz in Netrunner: [http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)
Not only is it not working, it's actively *worse.* So this kind of tells me that the problem doesn't come from Kwin or Compiz, it's OpenGL itself that just *refuses *to work.

---

### Post by KryoMouse on 2013-09-07
I only ever had problems with Kwin effects vs OpenGL when using the Nouveau driver. Upon installing the nvidia propietary drivers my system seemed to suddenly spark into life and work alright (discounting the wonky DPI settings for Plymouth and LightDM login manager); running on OpenGL and Raster Qt with a working cube.

Apologies if you've already moved away from default drivers but there's my experience and admittedly very quick fix.

---

### Post by BlacklightHalo on 2013-09-19
I've been using the default graphics driver for this computer (I've tried messing with alternatives before on various computers, each with disastrous results, so I'm a little gun-shy about that.) As I said it worked fine before restart and now it's fussing with me about using OpenGL. I read on someone else's thread discussing this on another Ubuntu site, that this is just a matter of the newly-implemented XRender compositor not having had its initial bugs/incompatibilities with the current version of Kubuntu worked-out yet.

If that's the case, it kinda makes me wonder - will this tend to happen generally frequently? (for instance, where the desktop cube or other effects won't behave themselves when either KDE or the compositing manager or something else pertinent to desktop effects is updated, forcing me to wait for it to be worked out within Canonical?)

@Nut-Kicker - That guide requires the use of CCSM which I've found is extremely dangerous and unstable, and I personally won't use it. The way I understand, CCSM is being phased-out in favor of the cube and other popular effects just being native to KDE. If you look in "Configure Desktop Effects> All Effects," you can see it's already there. I tried to put some screencaps in to illustrate but for some reason UbuntuForums' upload form won't play ball. Anyway they seem to be all there in the menu already, but they just don't work properly for everyone yet.

---

