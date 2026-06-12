---
title: "How do I disable Chameleon effect in Unity? 12.04"
date: 2012-05-11
forum: Desktop Environments
---

### Post by dilodicus on 2012-05-11
I've searched for an answer to this but nothing seems to work.

I'm running 12.04 and I love it, my only gripe is when I change my desktop background the launcher, dash, volume/brightness up/down and network notifications change colour to match the background image.

I've tried changing it back in CCSM but Unity will default back to it's choice of colour as soon as I close CCSM.

It seems this isn't unique to my system, but for what it's worth my specs are:
Dell n411z
intel i5 2430M
intel 3000 HD graphics (on CPU)
4GB DDR3 1333MHz
Ubuntu 12.04 x64

Does anyone know if there is a solution to this and/or if Canonical are looking at giving us the choice to disable it if there isn't a solution?

Many Thanks

---

### Post by dilodicus on 2012-05-11
Forgot to mention that I've tried MyUnity as well and it has much the same lack of effect

---

### Post by grahammechanical on 2012-05-11
The response of the Dash and the Launcher is down to the setting of the Dash blur. The Ubuntu Unity Plugin of CCSM under the Experimental tab will lets us set the the Dash blur to Active, Static, or None.

This should not affect the app indicator menus. They are controlled by the choice of theme.

What theme are you using? One of the default themes? Or a downloaded theme.

Themes that were suitable for older versions of Ubuntu are not now suitable for 12.04.

Regards.

---

### Post by dilodicus on 2012-05-11
Hi, thanks for the reply,

I installed a fresh install of 12.04 when it was in Beta1 an have just regularly updated since then, I use the default Ambiance theme.

The Dash Blur setting was set to "No Blur". I've tried it under "Active" and "Static" as well. Under each setting, as soon as I open the dash, click on the launcher or adjust screen brightness or volume using the laptop's hot keys the colouring reverts back to what Unity has decided the colour should be depending on my desktop background.

It's not the indicator app menus that the colour is changing on, rather the pop ups that appear when you adjust the volume/screen brightness using hotkeys, or establish a network connection or when a new track starts playing in rhythmbox. (as per screenshot)

Many thanks

---

### Post by Ghost_Mazal on 2012-09-22
I also find this irritating. But like the OP I can't find a way to disable this. What annoys me is that I am now forced to use only certain background images as some colors just don't work on the launcher and looks ugly on the launcher even though they look good as a background.

---

### Post by mc4man on 2012-09-22
It's finally been fixed in 12.10
There's no reason it couldn't be extended to 12.04 though hasn't as of yet.
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586)
[https://bugs.launchpad.net/unity/+bug/975350](https://bugs.launchpad.net/unity/+bug/975350)

So 12.04 users can wait it out, hope someone ppa's it, or patch & build unity themselves
(when I used 12.04 I always fixed this as the solution was known even before 12.04 released.

---

### Post by Ghost_Mazal on 2012-09-23
Well seeing as 12.04 is the official LTS it really should be fixed in 12.04. It would be the obvious and correct thing to do. Let's hope they do it.

---

