---
title: "A better application switcher plugin for compiz."
date: 2009-11-26
forum: Desktop Environments
---

### Post by tnvkrishna on 2009-11-26
hi all,
the application switcher plugin used by compiz
is rather ,I should say, useless.
It takes a little time to figure out exactly which
window is being pointed to by the plugin by pressing alt-tab.
the thumbnails shown are not as good,and the background of the
switcher menu is too transparent.

Any suggestions to circumvent this problem?

ubuntu 9.10
ccsm 0.8.2

regards,
krishna

---

### Post by yossell on 2009-11-26
Which application switcher plug in are you using? Compiz has quite a few choices. Have you experimented with different settings for the plug-in? changing opacity, enabling icons etc. At least on my system, the relevant window is brought into focus immediately on the desktop, so it's clear just by looking at the desktop which one is in focus. There are other switchers that you might prefer.

---

### Post by nyhm on 2009-12-07
I second this request. The flashy switchers are fun, but not practical (for me).

The "Static Application Switcher" seems to be the most basic. I'm even using the no-popup mode. However, it still causes two visual distractions:

[LIST=1]
[*]Backdrop shading and focus highlight.
[*]Noticeable blip as the screen is returned to "normal"
[/LIST]
I just want the "standard" window manager alt-tab bring-to-front behavior.

If I disable all compiz application switchers, alt-tab no longer works at all. The only way to overcome this is to turn off compiz entirely (System->Preferences->Appearance->Visual Effects->None).

a) Can the compiz supplied "Static Application Switcher" be made to not shade/blip?
b) Can normal window manager alt-tab be made to function without turning off compiz?

(By the way, I'm familiar with GNOME in Debian, but brand new to Ubuntu.)

---

### Post by akashiraffee on 2009-12-07
The goofiest one involves alt-ctl-up I think -- if there are three windows, you usually only get to choose from one of two.  I think that is a native gnome shortcut tho.

Don't use the **switch shifter** with "all windows", it's too confusing.  Use the Expo wall to select a workspace, then use the switch shifter with the windows only in that space.

Next Window
Previous Window
Next Window (All workspaces)
Previous Window (All workspaces)

The first two set hotkeys only show windows in the current space.   The selected one is clearly outlined black on white.

---

### Post by cyclopsface on 2009-12-23
If you turn Saturation, Brightness, and Opacity all up to 100, and put Zoom to 0, then your concerns will all be addressed except for the 'blip'.

I also hate the blip, but found this to be a workable solution for now.  It took me forever to discover the 'no pop-up' option, which was my major gripe.  Still wish I could just have default alt-tab though :confused:

---

### Post by nyhm on 2009-12-23
Thanks for the info, cyclopsface. Your concerns are identical to mine. First I wanted to get rid of the popup window, then the background shade, then the blip. I'm not sure I can live with that blip, but I'll give it a try again, with the shading disabled.

Does anyone know if the blip can be avoided? Is this a known bug?

---

### Post by karatedog on 2010-01-12
I'm not sure if I got it right, but I use Static Application Switcher, and I notice no 'blip' or whatever.
I checked that 'pop-up' you mention, and the only pop-up parameter I could change is the time Static App Switcher waits before popping up (this is 0 for me of course)
The only thing that is not configurable is the background opacity of the Static App Switcher, which is set to about 75% opacity.
So no 'blip', no 'pop-up' in my app switcher, quite usable.

---

### Post by nyhm on 2010-01-12
karatedog, I agree that Static Application Switcher is the most usable. However, I get a blip when the the applications switch. 

Here are some details, hoping anyone can shed any more light on the situation:

I have an ATI Radeon HD 4200 512MB (embedded on Gigabyte motherboard) using the ATI/AMD proprietary FGLRX graphics driver in Ubuntu 9.10.

Here is one way to reproduce the blip: Open two application windows and maximize one (e.g., maximize Firefox and open a non-maximized terminal on top). ALT-TAB rotates which window is up front, which works just fine while ALT is held down. While still holding ALT, bring the larger window up front (on top), then release ALT. For me, this causes a momentary (but very distracting) blip, when I can see both application windows before the front window is redrawn.

Without any knowledge of Compiz, my guess is that it is performing the ALT-TAB visual manipulation in some kind of graphic buffer. When ALT is released, the "fake" image buffer goes away, briefly revealing the "real" desktop, before the actual application windows can be commanded to restack themselves.

Please let me know if there is somewhere I could contribute this use case to fix this bug.

---

### Post by SecretCode on 2010-01-13
> **nyhm said:**
> Please let me know if there is somewhere I could contribute this use case to fix this bug.

You could try here: [Bugs in Compiz](https://bugs.launchpad.net/compiz) or here: [http://bugs.opencompositing.org/](http://bugs.opencompositing.org/)

---

### Post by nyhm on 2010-01-13
Thank you for the pointers, I shall check those sources and possibly enter a new bug.

**EDIT:** I've added my two cents to this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/325108](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/325108)

Maybe if other concerned parties comment there as well, the issue will get moved up from Low priority.

---

### Post by dmelliot on 2010-08-15
I too would love to know a way to enable the default (i.e. no compiz) alt-tab application switcher whilst keeping the other compiz options enabled.

The other app switchers all have their pros + cons, but I always find myself wanting the default gnome static switcher.  So much easier to identify the app you want than with any of the compiz switchers (esp. if you have 10+ windows open)

---

### Post by nyhm on 2010-08-16
I'm glad to hear this is still an issue for folks (er, that didn't come out right). I still watch this thread and the bug I linked for any resolution. I still do not run Compiz due to this issue.

---

