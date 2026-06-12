---
title: "Volume control going crazy"
date: 2009-02-06
forum: General Help
---

### Post by Antioch on 2009-02-06
Hi all.

I've recently installed Intrepid on my desktop and it works well. However I have a problem with the volume control - whenever I try to change it, the volume level slider goes crazy.

Let me try to explain it more clearly. When I open the volume applet in the tray and try to drag the slider, it will instantly go to zero and then rapidly fluctuate up and down to random locations - it never goes where I drag it to. The same thing happens when I scroll the mouse wheel up and down, and when I press the up and down volume buttons on my keyboard.

What is going on with my volume mixer?

I have an ASUS Xonar DX sound card, if that has any connection to it. It shows up in the device manager as "Asus Virtuoso 200" and as a "CMI8788 [Oxygen HD Audio]" controller. I believe the controller is accurate, but I'm not sure about the Virtuoso part.

Anyways, does anyone know how I can fix this? Not being able to control the volume is a show-stopper for me.

Thanks! Appreciate the help.

---

### Post by Antioch on 2009-02-06
I was poking around some more, and I think I've found the problem, so I'll document it here for those that need it in the future.

It seems that the volume control is set by default to control "Xonar DX." While this looks right, it is actually not. Change it to "AV200" or "PLayback: ALSA PCM" - these seems to work and not jitter.

Good luck!

---

