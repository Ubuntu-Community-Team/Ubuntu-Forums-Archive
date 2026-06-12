---
title: "Fullscreen Games, Pillarbox X.org ?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by aphirst on 2008-06-07
Right, I think this is an appropriate section to post this in.

I have a fair few games (both native and through WINE) which will only run in resolutions which are the aspect ratio 4:3; notably Wargus and Warcraft III.
My Laptop's LCD screen's ratio is 16:10.
When I run these games in full-screen mode, obviously the result is stretched O_o .
I was thinking earlier today "Is there some way to make X recognise that the game is not the same aspect ratio as the monitor, and to Pillar-Box to make it look right?"

(If you don't know what I mean; it's basically "Put appropriately sized Black Bars on the sides of the screen such that the output is squashed into the correct shape for the monitor" )

Perhaps this could be achieved by launching a separate X-session for the game; but I'm still clueless as to the implementation. Does anyone have any bright Ideas?

Thanks ;)

---

### Post by vytah on 2009-01-05
What's your graphics card?
If it's Intel, just
```
sudo xrandr --output LVDS --set PANEL_FITTING full_aspect
```
if you want 1024x768 to be stretched to fill vertically and leave black pillars (pillarboxes) on the sides (bad side: fuzzy pixels), or
```
sudo xrandr --output LVDS --set PANEL_FITTING full_aspect
```
if you want 1024x768 to be centered, with 1:1 pixel mapping and a black border all around (bad side: smaller resolutions get really smaller - 800x600 won't fill even 1/2 area of your screen)
(For separate monitor, use VGA instead of LVDS.)

I haven't bothered to test if this change is permanent or lasts only until reboot.

If you use ATI, look for aticonfig
If it's NVidia or else, I can't help.

---

