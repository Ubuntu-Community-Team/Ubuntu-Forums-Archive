---
title: "need 50Hz refresh rate for tv out"
date: 2006-02-19
forum: Desktop Environments
---

### Post by anatole on 2006-02-19
hi,
i have a compaq presario 2100 laptop (ati card), and i'd like to use it as a media player connected to my tv. The problem is that the tv needs 640*480 for resolution and 50Hz for refresh rate. the first one is not a problem, but i can only set the refresh rate to 60Hz in any resolutions.
My xorg.conf settings are:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```

i tried setting the VertRefresh value to 43-50, but i can still only choose 60 Hz. What should i do? Any help would be appreciated. :)

---

### Post by heimo on 2006-02-19
Try changing it back to 50 and create custom modeline for 50Hz. Add it to monitor section. 

```
# V-freq: 50.00 Hz  // h-freq: 24.74 KHz
Modeline "640x480" 17.62   640  648  672  712   480  480  481  494 
```
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by anatole on 2006-02-19
[QUOTE=heimo]Try changing it back to 50 and create custom modeline for 50Hz. Add it to monitor section. 

```
# V-freq: 50.00 Hz  // h-freq: 24.74 KHz
Modeline "640x480" 17.62   640  648  672  712   480  480  481  494 
```
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)[/QUOTE]

now a bunch of new resoultions appeared, but every one of them is still at 60Hz (setting it from xfce settings manager, i guess it doesn't matter...)

---

### Post by heimo on 2006-02-19
You probably also need to change HorizSync to something like below. However I have never tested using TV with computer (since 1980's), so this may be wrong. Also this may not work with regular display.
```
HorizSync    24-51
```

EDIT: Other possibility would be to try just the [FONT=monospace][/FONT]24.74 (without range).

---

### Post by anatole on 2006-02-19
tried both. still no luck :/ thanks anyway...

---

### Post by knalle on 2006-02-19
tv out in 50hz, getting 60hz? sounds like PAL/NTSC mixup somewhere?

---

### Post by anatole on 2006-02-19
[QUOTE=knalle]tv out in 50hz, getting 60hz? sounds like PAL/NTSC mixup somewhere?[/QUOTE]

i don't know. the tv is pal, i guess (i'm in Europe). The important thing is that it needs 50Hz while on the laptop, the default is 60Hz and i couldn't change it up to this point.

---

### Post by knalle on 2006-02-19
no, your tv in europe should get 60hz regardless of it comes from the laptop or not

---

### Post by anatole on 2006-02-19
[QUOTE=knalle]no, your tv in europe should get 60hz regardless of it comes from the laptop or not[/QUOTE]

hum. now that's interesting... :) i'll look through its specifications...

---

### Post by anatole on 2006-02-19
[quote=wikipedia]The term "PAL" is often used informally to refer to a 625-line/50 Hz (principally European) television system, and to differentiate from a 525-line/60 Hz (principally USA/Japan) "NTSC" system.[/quote]
so, i still need 50 Hz :)

---

### Post by knalle on 2006-02-19
ah, i knew it was a mixup somehwere, in my head :-)

---

### Post by heimo on 2006-02-19
I think I have a solution.         

Here's a new Monitor section (found via Google, tested on my monitor):
```

Section "Monitor"
        Identifier   "TV"
        HorizSync   31.5-90
        VertRefresh 30-60
        ModeLine "640x480PAL"   29.50       640  676  680  944   480 530  535  625
EndSection

```

Be sure to change Monitor value in Screen section to TV and in the same Screen section change Modes line to:
```

Modes           "640x480PAL"
```


Worked on my monitor - got a 50Hz 640x480 resolution/refresh rate. Hopefully this works for your TV, too.

---

