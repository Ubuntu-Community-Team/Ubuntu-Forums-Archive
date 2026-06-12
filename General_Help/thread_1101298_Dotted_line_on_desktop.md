---
title: "Dotted line on desktop"
date: 2009-03-20
forum: General Help
---

### Post by pcolbeck on 2009-03-20
Not sure which forum this should go in so will try here. I am running 8.10 with an Nvidia 7600 graphics card using the latest Nvidia drivers. Over the last couple of days I have noticed a dotted line on the desktop under the top panel. It's not right across the screen its broken up a bit. It show sup in any application you move over that bit of the desktop too. 
Its not the monitor as if I change the resolution the line moves but stays in the same position relative to the panel. It's also there in both GDM and KDM. It doesn't seem to be there before X starts, for example if I go into the PC BIOS.
I have tried reverting back to an older Nvidia driver and that had no effect.
Not sure if this is the graphics card starting to fail or a problem caused by a recent update.

Thanks

Pat

---

### Post by todak on 2009-03-20
Is the line bright and kind of "sparkly"? If so, you better get another video card quickly. I had the same thing happen and before long the whole screen was full of bright sparkly outlines at the edges of fonts, widgets, etc., even at the computer boot screen (the "DELL" logo). I swapped video cards and the problem was solved. But I waited TOO long to change the card as it had damaged my monitor :( (all kinds of random lines on the screen with new card, but "sparklies" were gone.), so had to get another monitor too! Old card on new monitor = mess on screen :frown:. New card on new monitor = clean screen. \\:D/ New card on old monitor = mess.

---

### Post by pcolbeck on 2009-03-20
Thanks. I will order a new graphics card. Luckily due to Moores law I can get an 8000 series Nvidia card for £25 now when the 7600 series one cost me £80 three years ago :)

---

### Post by pastalavista on 2009-03-20
Before you change video cards, try this in terminal
```
sudo /usr/sbin/update-initramfs -uv
```
and then reboot. it fixed some graphics glitches for me once

---

### Post by pcolbeck on 2009-03-20
Didn't work. Oh well it was worth a shot.

Thanks

Pat

---

### Post by pcolbeck on 2009-03-24
A new Nvidia 8500GT graphics card didn't fix it either. I can see the weird line before X loads now but changing screen resolution still moves it. At 1680x1050 its about 1cm form the top of the screen and at 800x600 its about 5cm form the top of the screen.

---

