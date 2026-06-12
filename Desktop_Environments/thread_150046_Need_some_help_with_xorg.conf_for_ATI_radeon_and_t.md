---
title: "Need some help with xorg.conf for ATI radeon and tv out situation."
date: 2006-03-25
forum: Desktop Environments
---

### Post by rdking on 2006-03-25
Sorry guys, have been trying for a while to try and figure out how to do it on my own, but just can't seem to get it all working.  If anyone has a setup, where their xorg has 2 didplays set up, one for their monitor and one for there TV, and are using the ATI 8.2 series ddrivers which I could use as a guildline to preparing my own, I would Really appriciate it.  Tried the Aticonfig, but my tvout ends up flicking and with no colour.  Pretty sure its due to incorrect refresh rates or resolutions, which is why I want to set up a seperate display(screen) for my tv and give it the proper numbers.  Thanks in advance.

ryan

---

### Post by claes on 2006-03-25
I don't have this setup myself. But I had something simular on my old machine. See what happens if you set the option composite to true in your /etc/X11/xorg.conf in the device setting. Not sure if this will fix the problem. But if I remember correctly that was what I did to get it working.

Claes

---

