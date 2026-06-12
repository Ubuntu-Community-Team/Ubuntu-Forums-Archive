---
title: "Widescreen pushed to the right (left part of screen blank)"
date: 2007-04-20
forum: Desktop Environments
---

### Post by lhmathys on 2007-04-20
I have tried to fix this but thus far have had no success.  My video card is an Intel 845G chipset and the monitor is an LCD Hanns-G JW199D 19" widescreen.

I used 915resolution to finally get the monitor into 1440 x 900 mode by patching the 1280 x 1024 mode and adding the modeline to my xorg.conf.  The monitor is finally in the correct resolution, but the Ubuntu desktop is pushed to the right.  This leaves about a 4" blank area on the left part of my screen and the desktop has lost a good portion of the right side (I'm working on just the left side for now.)

If someone has been able to get the Intel 845G chipset to work, please help!!!  I'd love to be able to use this monitor instead of switching to an old 17".

Here is the relevant information:
915resolution output:
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $38a
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1440x900, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1440x900, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1440x900, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


And here is my xorg.conf:

---

### Post by RedSquirrel on 2007-04-20
Does your monitor have an option in the onscreen display similar to "Auto Image Adjust"? On mine (a Viewsonic) I can just select that and it will make the necessary adjustments.

---

### Post by lhmathys on 2007-04-20
Yes, but that didn't work either.  Thanks for trying, though.

I still can't get the desktop session to fill the entire screen when the monitor resolution is set to 1440 x 900.

This is driving me nuts, and I hate having to go back to 1280 x 1024 on this widescreen monitor, it looks terrible.

---

### Post by lhmathys on 2007-04-20
I should also be more specific about my on board video card:

It's the Intel 82845G (and from what I'm reading, not a lot of people are having success with this video card with a widescreen monitor.)

I may just end up buying a new video card.  :(

---

### Post by RedSquirrel on 2007-04-20
I notice in your xorg.conf you have 

```
VertRefresh           60
```Have you tried putting the appropriate range for your monitor, instead of a specific value? Not sure it will help your screen being off-center, but it's one thing that is a bit different from a typical setup.


**EDIT**

Where did you get those values for DisplaySize?

```
DisplaySize     410 257
```For DPI of 96 I used:

```
DisplaySize     381 238
```You might also try another modeline. The ones generated [here]("http://www.bohne-lang.de/spec/linux/modeline/") give *slightly* different values.

Have you seen [this guide]("http://ubuntuforums.org/showthread.php?p=454217")?


I've seen a number of people having issues with that graphics hardware. 

In my case, I have an old ATI card and it would not generate 1440x900 without the use of the Virtual line in xorg.conf (as you have done). When I used that line, the display didn't look all that impressive (though that may have just been the overall poor quality of the monitor itself). If you get it to work, you'll have to judge for yourself the quality of the fonts and so on. I ended up swapping the 19" widescreen for a traditional 19" (1280x1024).

---

### Post by lhmathys on 2007-04-23
Thanks for the help.

I was able to minimize the black band on the left of the screen to only about 3/8" with the manual screen adjustments pushed as far to the left as it would let me.  At least this is manageable.  I'm sure the problems I'm having are due to some driver issues with this video chip.  I'll probably just go buy a new video card soon.

---

### Post by RegularSlinky on 2008-01-12
Hello. I have a Hanns-G HG216D 1680x1050 and mine did the same thing. The display appeared at the right hand side of the monitor with a big blank dark area. I don't honestly know what causes this but I have managed to fix it. I'm not sure if its the video drivers or the monitor settings.

I *think* its the video drivers as when I updated to the proprietary drivers (and then hit the A button on the monitor) the problem went away. After install I did system update with Update Manager, switched on drivers (for my GeForce 3 card).

Once you've done that you can just choose the default 1680x1050 LCD monitor from the settings. Be sure to choose sub-pixel fonts from Appearance -> Fonts as well otherwise your font display will look awful (but it's still hard on the eye). I suspect you'll only get the best results with an HDMI card/cable.

You may want to get Automatix as this will download some proprietary software that you might want. 

Cheers. :)

---

