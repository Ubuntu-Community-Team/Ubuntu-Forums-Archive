---
title: "my display won't sleep!"
date: 2006-01-04
forum: General Help
---

### Post by obontu on 2006-01-04
hey everyone
i'm using ubuntu 5.10 and enjoying every moment of it
i got a 2800 athlon xp with 512 ram
(not a laptop)
and i'm dualbooting with xp cuz my family needs it
anyhow, when i'm using xp, i can set it to sleep my display after
a few mins
but when in ubuntu, i go to system-> preferences-> screensaver
and advanced -> display power managment and when i tick it and try to use the standby option, it won't work
if i exit and then come back to check it again, it's unticked :(
can someone help please?

ok solved you can delete this thread

---

### Post by z_diver on 2006-01-04
Obontu, do you mind telling us how you fixed it?

I have a related issue.  My Sony hx73 lcd monitor won't turn completely off, black, using powersave functions.  Anybody know why?  Works fine on a few of my Ubuntu laptops.

Monitor: Sony SDM HX73
ATI Technologies, Inc. Radeon 9600 (R300 AP)
video driver: ATI fglrx
breezy 32 bit

---

### Post by AirIntake on 2006-02-12
Here's what i did to get it to work. Even though display power management in Screensaver was enabled and set to 1min standby, 2min suspend, and 3min off, nothing would happen until I set my set my screensaver mode to 'Blank Screen Only' and then set it to 1min same as my standby time. Now the screen goes into standby at 1min. The enable power management tickbox will disable itself if you try to set suspend and off times to 0 while keeping standy at a value. That's why I have my numbers at 1min, 2min, and 3min, because if I set it to 1min, 0min, 0min it would disable. I think you can do stuff like 0min, 0min, 1min, and 0min, 1min, 2min etc though without it disabling. Of course I'm just using numbers that I'm using, you can use values other than 1, 2, and 3 min. Just make sure that the blank screen timeout is set to the same value as the suspend or lowest used power function. ie. if settings are 10min, 15min, 30min, blank screen should be 10min. If settings are 0min, 15min, 30min, then blank screen should be 15min.

I don't really know what I'm talking about but this seems to work fine for me.

---

### Post by z_diver on 2006-02-12
Thanks for the reply but it didn't work for me.  I played around with it a bit and set everything just the way you mentioned... although the screen went blank, it did not go black as if it's off(well maybe for 1 second but then the backlight turns on again).  Since it works on my laptop, i figure it may have to do with hardware and drivers.

ATI Radeon All in Wonder 9600 128mb
ATI fglrx driver
Sony SDM HX73 monitor
iogear miniview III kvm
dell 400sc
Breezy

---

