---
title: "Background turns to ribbons, reset X, now nothing"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by daynah on 2007-10-24
Last night I was on my desktop just fine. I turned off the monitor and went to bed. I wake up, turn on the monitor and shake the screen awake (there's also a screen saver, that might be important), and, though all of the windows are fine, the wallpaper is only "half" there. As in, a horizonal strip or ribbon can be seen, then a horizontal black strip, then another strip of the wallpaper, and again until the end, each maybe an inch tall. Also, the menu at the top and bottom (I have them set basically to default, just changed the theme), has turned to black except for the places that has "stuff" on it.

I think, "Eh, I just X just... decided to break. That's... pretty weird." And I Ctrl+Atl+Back. I log in just fine, and when I hear the music, there's nothing but black and my mouse is an X. Darn.

I have compiz installed. I installed and got that working maybe three or four x resets ago, though. I was having the "no borders" issue and I solved it by installing, I believe the package was called xglsession-xgl though that sounds a bit redundant for a name, maybe someone knows what package I'm talking about.

The only thing "fishie" (not checking email, im, ect.) in that session though, was I installed Pidgin 2.2.1 from source, and I haven't the faintest idea how that could mess this up.

I've had so many problems with X on my desktop :( I hope there's an easy fix, 'cause I've not the time for either a big issue or a clean install. Blah!!

EDIT: Oh I have some cheap nvidia. I don't know what it is but I know I got it when ATI was the loser, and the card is compatible. Now ATI flipped on me. They waited just to catch my disloyalty! Arg!

EDIT: Zomg. I turned it on again and after being an tho black screen with the X for a second it started working. Dear Computer, I have the money to invest in a ghost hunter. Just let me know. Your loving Mistress, Daynah.

---

### Post by Jose Catre-Vandis on 2007-10-27
If you have an nvidia card installed you do not need XGL.
Get to a command prompt (CRTL+ALT+F1...)
```
sudo apt-get remove xserver-xgl
```
reboot/restart - should get you back in

---

