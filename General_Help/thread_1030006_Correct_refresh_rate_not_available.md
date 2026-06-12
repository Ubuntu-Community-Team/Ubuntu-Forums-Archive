---
title: "Correct refresh rate not available"
date: 2009-01-04
forum: General Help
---

### Post by Geezle on 2009-01-04
I just got myself a shiny new monitor, but the the monitor auto detection isn't quite getting it right.  I have the correct resolutions available, but I can only get a refresh rate up to 51hz, but it should be 75hz.

I know I need to set it up in xorg.conf and I've been reading about it, but I just can't seem to get my head around what I need to do.  

The monitor is a Samsung SyncMaster 953BW (specs are here[http://http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS19AQWKF/XAA&fullspec=F]("http://http://www.samsung.com/us/consumer/detail/spec.do?group=computersperipherals&type=monitors&subtype=lcd&model_cd=LS19AQWKF/XAA&fullspec=F"))

If somebody could help me out with this, I'd really appreciate it.  I tried going through a tutorial on here, but I ended up kicking myself into low graphics mode.  I did use the modeline utility and came up with this:
```
 
  Horizontal Resolution:   1440 
  Vertical Resolution:      900 
  Vertical Refresh Rate:   56.00 Hz 
  Horizontal Refresh Rate: 52.15 KHz 
  Dot Clock Frequence:     95.13 MHz 

 # V-freq: 56.00 Hz  // h-freq: 52.15 KHz
 Modeline "1440x900" 95.13  1440 1488 1608 1824   900  900  902  931 

``` 
But I'm not entirely sure what to do with it.

I'm trying to get the monitor to do 1440x900 @ 75hz.

Any help would be greatly appreciated :)

---

### Post by Sef on 2009-01-04
What's your video card?

---

### Post by Loosewheel on 2009-01-04
Per Samsung:
"The optimum refresh rate for all Samsung LCD monitors is 60 Hz".

---

### Post by Geezle on 2009-01-04
> **Sef said:**
> What's your video card?

The video card is an onboard GeForce 6150.  I haven't found the exact refresh rate it's capable of yet, but now that I'm awake again, I'm still looking.  Should be able to give me better than 51hz at any rate.

---

### Post by Geezle on 2009-01-04
> **Loosewheel said:**
> Per Samsung:
"The optimum refresh rate for all Samsung LCD monitors is 60 Hz".

Thanks for replying in this thread, and the other.  Maybe you were having the same issues I was last night?

Anyway, the little literature that came with the monitor tells me that optimum viewing is 1440x900@75hz, and when I first hooked up the monitor, it popped up a display telling me the same thing, this is why I'm shooting for 75hz.


As a sidenote, as my display sits right now, my display seems to be kinda washed out.  Could this be related to the refresh rate also?

---

### Post by Geezle on 2009-01-04
> **Loosewheel said:**
> Per Samsung:
"The optimum refresh rate for all Samsung LCD monitors is 60 Hz".

Actually you're right.  After reading the manual, it says the optimum is 1440x900@60hz and maximum is 1440x900@75hz.  The little OSD on the monitor still tells me that optimum is 75hz, which is where I got that number from in the first place.  I never would have thought adding a new monitor would be such a hassle!

Regardless, I'd really like to get it to at least 60hz...hopefully that'll fix my washed out display.

---

### Post by Geezle on 2009-01-04
Ok, now this is driving me batty!  I have the correct refresh rate options (60Hz and 75Hz) showing up in my NVIDIA X Server Settings, but they won't pass over to the monitor resolution settings.  If I change the refresh in the NVIDIA setting, it gives me an option of 98Hz (wtf? :confused: ) but when I try to set it to that in the resolution setting, it just kicks down to 50Hz or 51Hz.  What am I missing?

---

### Post by lsutiger on 2009-01-14
For a quick fix try sudo displayconfig-gtk...I am having the same problem, but fixed it that way for every X-restart(log off/restart/power, etc).

I am still looking for a solution. [Here is my thread]("http://ubuntuforums.org/showthread.php?t=956541").

My settings just will not save, so I have to run the display command every time.

---

### Post by kororke on 2009-01-17
I too am having similar problem with BenqFP553 monitor. The Auto xorg config for the display finds ridiculous parameters. and any attempt to force things with "startx" produces a long error message ending in "no screens available".
Adding the correct "monitor" section to Xorg.conf was no solution.
Previous versions of Ubuntu (pre auto conf)produced unworkable v and h refresh figure but with pico these could be edited to correct values, and from then on all was fine.
The video card has nothing to do with this as I have used 2 entirely different cards.
SURELY THERE MUST BE A WAY OF PERMANENTLY FORCING THE CORRECT VALUES!!!
The long and short is, I cannot use Ubuntu. in its present form.

kororke

---

