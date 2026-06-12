---
title: "astromenace can't detect my screen resolution."
date: 2007-01-23
forum: Gaming &amp; Leisure
---

### Post by onesojourner on 2007-01-23
I just installed astromenace ([http://gaming.gwos.org/index.php?option=com_content&task=view&id=130&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=130&Itemid=63) )
and I get the error: Could not select resolution. Fatal error.

the screen resolution on this laptop is 1680x1050.

---

### Post by Rytron on 2010-06-13
I can play astromenace. However it I cannot change the resolution from the default for astromenace which is 1024x768. My resolution is 1360x768.

---

### Post by Rytron on 2010-06-13
This thread has got a new lease of life after 3 and a half years!

I wonder is there a way to force astromenace to run in a window of 800x600? At lease that way, all the options would be viewable!

---

### Post by hikaricore on 2010-06-13
You didn't need to dig up two ancient threads and ask a stupid question twice.
Would have made more sense to just make a new one...

---

### Post by vagrale13 on 2010-06-27
> **Rytron said:**
> This thread has got a new lease of life after 3 and a half years!

I wonder is there a way to force astromenace to run in a window of 800x600? At lease that way, all the options would be viewable!
If you see the archive **astromenace** the path is* /usr/games/astromenace*

```
#    --mode=N - set the game windows mode and resolution (forced)
#    where N is number from 0 till 17:

#    Fullscreen modes
#        0: 640x480x16
#        1: 640x480x24
#        2: 800x600x16
#        3: 800x600x24
#        4: 1024x768x16
#        5: 1024x768x24
#        6: 1280x1024x16
#        7: 1280x1024x24
#        8: 1400x1050x16
#        9: 1400x1050x24
#        10: 1600x1200x16
#        11: 1600x1200x24

#    Windowed modes
#        12: 640x480
#        13: 800x600
#        14: 1024x768
#        15: 1280x1024
#        16: 1400x1050
#        17: 1600x1200
```for test open *astromenace *with terminal and just change the number with your resolution
```
 /usr/games/astromenace --mode=NUMBER
```then edit the menu, and change the command where open *astromenace*! :D

---

