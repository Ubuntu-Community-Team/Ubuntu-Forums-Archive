---
title: "Upsidedown Desktop"
date: 2011-04-27
forum: Desktop Environments
---

### Post by klausner on 2011-04-27
Help! My lucid desktop has suddenly started coming up upside down, flipped 180 degrees vertically. How can I get back to normal? 
[IMG]http://i52.photobucket.com/albums/g13/tanuki-kage/Emoticons/panic.gif[/IMG]

---

### Post by inobe on 2011-04-27
go to system> preferences> monitors.

change the rotation.

---

### Post by klausner on 2011-04-27
> **inobe said:**
> go to system> preferences> monitors.

change the rotation.

Good idea, Unfortunately, it doesn't help. Still upside down :(

---

### Post by ibbill on 2011-04-27
you may want to give this a try also.

Try using the keyboard combination, "Control + Alt + Up Arrow Key". Control + Alt along with one of the arrow keys is a fairly common rotation hot-key configuration and may just do the trick.

---

### Post by Copper Bezel on 2011-04-27
Not on Gnome. Coincidentally, that works on my machine, but not by default. = )

Try running ```
xrandr -o normal
``` and, for the hell of it, ```
xrandr -o inverted
```

---

### Post by klausner on 2011-04-27
> **Copper Bezel said:**
> Not on Gnome. Coincidentally, that works on my machine, but not by default. = )

Try running ```
xrandr -o normal
``` and, for the hell of it, ```
xrandr -o inverted
```

Tried ```
xrandr -o normal
``` based on another thread. No results.

---

### Post by klausner on 2011-04-28
> **Copper Bezel said:**
> \and, for the hell of it, ```
xrandr -o inverted
```

Close!!! *xrandr -o inverted* gets the desktop right-side up. Unfortunately, everything is then backwards, including all text. Now that I have had a chance to read *man xrandr* without needing a mirror, I need to try *xrandr -x* next.

*Edit: *Tried -x, and it did indeed "reverse" the text back to normal. But the menu bars are still on the wrong side of the screen, the mouse works backwards in vertical movements, and worst of all the places where you need to click on things are not where the display shows them (they are in the original, screwed up positions).

Gah!! could my X config be screwed? How do I straighten this out, short of another re-install?

---

### Post by Krytarik on 2011-04-28
Although that all obviously doesn't fix the original issue, how about that then?:
```
xrandr --output OUTPUT --rotate inverted
```Yeah, I know that you tried apparently the same before through the GUI.

Note: It's kinda fishing in the dark when I suggest those commands, because most 'xrandr' commands don't work at all with my proprietary Nvidia driver.

---

### Post by bodyguard on 2011-04-28
Isn't it simpler just to turn your monitor upside-down?

---

### Post by Krytarik on 2011-04-28
> **bodyguard said:**
> Isn't it simpler just to turn your monitor upside-down?
:popcorn::D

Especially not if you are using a CRT, with some if not most LCDs you may have your difficulties, too.

---

### Post by Krytarik on 2011-04-28
I just yet noticed your edit. It seems like we actually have to solve this the usual way now, by finding the cause and fixing it. ;-)

What version of Ubuntu are you running?
What video card/chip do you have?
What driver are you running?
How did you install those?

---

### Post by klausner on 2011-04-28
> **bodyguard said:**
> Isn't it simpler just to turn your monitor upside-down?

Hard to do with a laptop. Also, the display is upside-down AND reversed.

---

### Post by Copper Bezel on 2011-04-28
The sarcasm is appreciated, but about that chipset? = ) Also,

> Edit: Tried -x, and it did indeed "reverse" the text back to normal. But the menu bars are still on the wrong side of the screen, the mouse works backwards in vertical movements, and worst of all the places where you need to click on things are not where the display shows them (they are in the original, screwed up positions).

 Gah!! could my X config be screwed? How do I straighten this out, short of another re-install?

How did the mouse move originally? Were the axes consistent with those of the display despite the flipped vertical axis of the display itself?

Edit: > Now that I have had a chance to read man xrandr without needing a mirror,

Still cracking up at this one. = )

---

### Post by klausner on 2011-04-28
> **Copper Bezel said:**
> How did the mouse move originally? Were the axes consistent with those of the display despite the flipped vertical axis of the display itself?

Mouse movements were normal, although the click-points (for lack of a better term) were not where displayed.

---

### Post by s_aldinger on 2011-04-29
This happened to me after I upgraded from 10.10 to 11.
I've got a ATI HD 3400 on my workstation.

I had to change my driver to fbdev and disable the "desktop effects" in KDE so I could load the radeon drivers without this issue.

Then after changing the driver back to radeon, I noticed my vmware workstation was crashing on startup of the vmguest. looking into this error pointed to a graphics issue. 
Since I compile all my own kernels and I was still using my old one, I knew the problem must be with the xserver.

So I loaded up glxinfo and discovered that xorg was using the nvidia glx drivers! There was my problem! During the upgrade it installed all the nvidia drivers onto my system. Removing them has since fixed all the issues.

---

### Post by klausner on 2011-04-29
> **s_aldinger said:**
> This happened to me after I upgraded from 10.10 to 11.
I've got a ATI HD 3400 on my workstation.

I had to change my driver to fbdev and disable the "desktop effects" in KDE so I could load the radeon drivers without this issue.

Then after changing the driver back to radeon, I noticed my vmware workstation was crashing on startup of the vmguest. looking into this error pointed to a graphics issue. 
Since I compile all my own kernels and I was still using my old one, I knew the problem must be with the xserver.

So I loaded up glxinfo and discovered that xorg was using the nvidia glx drivers! There was my problem! During the upgrade it installed all the nvidia drivers onto my system. Removing them has since fixed all the issues.

I've got an nVidia Card and the built in Intel graphics. nVidia drivers have been nothing but trouble. I suspected that xorg might be the culprit somehow.

---

### Post by Krytarik on 2011-04-29
> **klausner said:**
> I've got an nVidia Card and the built in Intel graphics.
Ok, that's a start then. My questions in post #11 are still standing, if you want me, or anyone else, to be able to help solving this.

---

### Post by klausner on 2011-04-29
Too late for me. I couldn't put up with the unusable system, and reinstalled.

---

### Post by Krytarik on 2011-04-29
> **klausner said:**
> I couldn't put up with the unusable system, and reinstalled.
And the issue apparently didn't re-occur there. Ok.

---

### Post by klausner on 2011-04-29
> **Krytarik said:**
> And the issue apparently didn't re-occur there. Ok.

Different issues. If I could afford a new system, I'd dump nVidia in a heartbeat,

---

### Post by Krytarik on 2011-04-29
> **klausner said:**
> I'd dump nVidia in a heartbeat,
But not for the sake of AMD, since it turned out that they are supporting their cards/chips with the proprietary driver only some few years. Although it isn't that good anyway. But because of the ceased support the open source drivers (OSED) are getting developed even faster than the open source driver for Nvidia cards/chips (Nouveau), they are now even included by the just released Natty 11.04.

For example, my Nvidia card is some 10 years old, and is still supported by the proprietary driver, while the ATI card in my mom's machine is some 5 years old, and after uprading from 7.10 to 10.04 she can only use the still-in-development OSED.

Or are you thinking about an Intel onboard chip?

---

