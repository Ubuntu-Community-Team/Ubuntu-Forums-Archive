---
title: "strange compiz maximize size (smaller than screen!)"
date: 2007-10-26
forum: Desktop Effects &amp; Customization
---

### Post by mega on 2007-10-26
for some reason when I maximize a window it only uses 3/4 of my screen

compiz seems to think the left 3/4 is all the screen I have

running an intel gma950, ccsm,general,display,outputs has the correct setting

1680x1050+0+0

that's the resolution that I'm running


couple pictures of what it's doing, this is as big as 'maximize window" will go

I can restore window smaller, and drag it to the corners, but it's kind of annoying watching DVD's, it wont let me do fullscreen

[IMG]http://www.geekopolis.com/gallery2/main.php/d/6692-2/strangestickystuff.png[/IMG]

[IMG]http://www.geekopolis.com/gallery2/main.php/d/6689-2/maximized.png[/IMG]

---

### Post by mega on 2007-11-06
bump

still cannot watch movies on my ubuntu pc

I believe compiz is seeing the resolution of my laptop lcd as the max, instead of the resolution of my external lcd as the maximum

it's pretty pathetic that this does not work

---

### Post by dentaku65 on 2007-11-06
Did you enabled  Workarounds plugin?

---

### Post by mega on 2007-11-06
it's enabled, seems to have defaulted that way

---

### Post by waldorf on 2007-11-26
I've got the exact same issue. Not a show stopper, but not good.

---

### Post by mega on 2007-12-05
still having the same problem

it's getting old not being able to watch DVD's full screens

[IMG]http://farm3.static.flickr.com/2243/2089658328_291826538b_b.jpg[/IMG]

---

### Post by mlissner on 2007-12-07
same here. I'm sure it's a laptop thing on my end.

---

### Post by sssmasi on 2007-12-13
I had the same problem... it seems like compiz has the wrong idea of what the screen resolution is... All i did, and it fixed it for me was change my resolutions down to 1024 x 768. After that i changed it back to the highest res setting and PRESTO it WORKED.

im using fedora 8 mind u... i dont see why it shouldnt work though if is the exact same problem

---

### Post by el escocés on 2008-01-29
Same thing happens to me, I have the external monitor set to 1280x1024 but the window only maximises to 1280x800 (my laptop resolution). 

Tried what was mentioned, by setting the resolution lower then higher again and no luck.

Any ideas?

---

### Post by nfox on 2008-03-08
If any of you are still having troubles, let me know. Tell me the drivers you have (Intel, Nvidia, ATI, etc) and if you have XRandR enabled. 

I have a laptop with an Intel onboard and plug it in at work to a desktop LCD. Maybe it was the fact that I installed it with the monitor plugged in, I don't know but my Xorg.conf file has the monitor's name but the specs for the laptop monitor. Therefore the screens are 'clones' but respective to their resolutions.

Long story short, you should try to first remap your X screen to determine proper configuration. 
When I go to work, I run this line and it puts the desktop monitor 'above' the laptop's:

```
xrandr --output LVDS --pos 1280x0 --output VGA --auto --above LVDS
```

When that's done, my Compiz cube is looking like a cylinder of dual screen goodness. Modify this as necessary, I've shown mine as an example for your compatibility. Here, **LVDS** = Laptop Display and **VGA** = Regular VGA and is what you're probably going to use. 

Use 
```
xrandr -h
```
for usage. Resize your screen bigger/smaller and such until it fits. You can poll the status by running 'xrandr' by itself. When you have the resolution that worked, edit your xorg.conf for future boots.


Anyone with a laptop plugged into an external monitor, use my code above with your resolutions and anyone else play around with the parameters.

---

### Post by drkbts on 2008-03-25
I have a similar problem (just installed Ubuntu 8.05 beta. on a HP4200) with an external 1920x1200 display.

Withbvisual  effects turned off: mo problem.

With visual effects turned on: windows to the left are maximized to about the top left quadrant of the screen. Windows a little bit to the right of the main screen (crossing the mid-lilne), are properly maximized. Somehow, Compiz is has some weird idea of picking up screen resolutions.

---

### Post by Zorael on 2008-03-25
What about that field in General Settings, on the tab where you set Number of Desktops, Virtual/Horizontal Desktop Size, etc? That 640+480+x field.

I remember setting it up erroneously whereupon I experienced what you're describing. Windows not maximizing to the full desktop area.

Try replacing the relevant numbers to the resolution you use. I don't remember the exact syntax; I'm on a l0sedows machine atm.

---

