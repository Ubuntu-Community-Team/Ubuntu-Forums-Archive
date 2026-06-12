---
title: "razer copperhead mouse sensitivity too high! (or accel)"
date: 2006-07-10
forum: Gaming &amp; Leisure
---

### Post by quick on 2006-07-10
hi ubutu-mates! :)

i'm happy to say that i'm back to using linux i think in ubuntu i've found what i waited for to switch :)

well well i got all the games working that i want to play but i have a problem with my mouse.

i play quake and cs and my mouse is TOO fast really. its soo bad i cant hit anyone because i cant aim.

i set sensitivity 1 in both games but its still too fast
playing in windows i have no problem with this sensitivity but i think thats
something like mouseaccel from Xorg 

i tried xset m 1 1 but this doesnt have impact on the game - the speed doesnt change :(

does anyone have a suggestion how to get lower speed or NO ACCEL
i'd like to have mouseaccel completely disabled

also copperhead supports 1000hz mouse polling rate - 
i changed the /etc/modprobe.d/options 
option usbhid mousepoll=1 
like a guide said and i can see cat /sys/.../usb/driver/modules/options/mousepoll is set to 1 so it should be right.

but i have a tool (called evhz) to check the hz and it always says 500hz maybe the tool is wrong but i cant feel the 1000hz like in windows.

anyone got experience with the hz changing and can tell me how to change it to 1000hz? :)

thanks in advance
quick

---

### Post by %hMa@?b&lt;C on 2006-07-10
if you are using gnome, did you dry ```
gnome-mouse-properties
```
to change the sensitivity?

---

### Post by quick on 2006-07-10
thanks for your help
i tested it just now but it doesnt effect the quake mouse accel/sens :(

---

### Post by quick on 2006-07-11
just some info i found out

xset m 1 1 / 0 0 

IS changing mouse behaviour in WINE (cs, wc3...) :) thats nice :) just quake3 is way too fast 

maybe i will get a good mouse feeling on linux someday :)

---

### Post by Perfex on 2006-07-11
[http://razertool.sourceforge.net](http://razertool.sourceforge.net)

I have a diamondback plasma so I cant use, but maybe it will help you

---

### Post by quick on 2006-07-12
thanks for your help and the url 

i already used that tool but it just changes the dpi :) i mean the mouse profiles 

btw diamondback is a really good mouse :)

---

### Post by Perfex on 2006-07-15
Err late response, Sorry to hear that wont help.
Been using Razer since the Original Boomslang which I still have

---

### Post by quick on 2006-07-15
i've razer since boomie 2000 but that was damaged from the day i bought it (sadly.)

---

### Post by jonesvb on 2007-02-22
I think this comes late:

To have propper sens in quake engine games you could try to set the console var in_mouse to 2 or 3.

Maybe this helps. I dont know the exact value, but the name of the var shoult help you googling


jones

---

