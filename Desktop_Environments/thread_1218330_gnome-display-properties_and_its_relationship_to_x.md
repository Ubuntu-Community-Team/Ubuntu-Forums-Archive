---
title: "gnome-display-properties and its relationship to xorg.conf"
date: 2009-07-20
forum: Desktop Environments
---

### Post by prioret on 2009-07-20
I have a dell mini 9 and a E228WFP display. I'm having a real hard time getting the external display at the correct res. When I do get it at the correct res, the window manager is freaking out and not drawing the window elements. When I try to reload the window manager, the screen goes all white.

So generally, getting the correct res has become a cluster.

I know X pretty well and in the past have been comfortable editing the xorg.conf, but it seams that gnome-display-properties wipes xorg.conf.

Does any one have a sure fire way to get the display at the correct res, and having the window manager (comvis) behave?

---

### Post by Dave_Connor on 2009-07-20
Have you tried opening a terminal and enter "xrandr" and see what it puts out ? Then you can edit xorg.conf and set up display section under "Screen" section. Like an example of my xorg.conf on my laptop below. 
```
Section "Screen"
Identifier      "Screen"
Device          "Laptop"
Monitor         "Mon"
SubSection "Display"
     Modes "1200x800"
EndSubSection

```

---

