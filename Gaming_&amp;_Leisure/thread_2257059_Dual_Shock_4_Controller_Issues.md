---
title: "Dual Shock 4 Controller Issues"
date: 2014-12-16
forum: Gaming &amp; Leisure
---

### Post by rbuanno on 2014-12-16
I can't seem to get this controller to work with my dolphin-emu or ingame on steam.
It works however in steam big picture. 
jstest shows js0 and that moving joysticks and pressing buttons has values (its responive)

What am I missing here?

I've been reading that it might have to do with events and / or SDL layers or something?

I've been reading this... [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/410187](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/410187)

Not sure how to recompile my SDL2 so it prefers js0, Can anyone show me how?

Tried putting [COLOR=#333333][FONT=monospace]SDL_JOYSTICK_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]DEVICE=[/FONT][/COLOR][COLOR=#333333][FONT=monospace]/dev/input/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]js0 in my /etc/enviroment file and rebooted...
[/FONT][/COLOR]Didn't make a difference... D:

Can someone offer me some help?

Much appreciated,

Ronald

---

