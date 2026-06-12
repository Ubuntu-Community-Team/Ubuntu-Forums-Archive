---
title: "Looking for stable Nvidia series 8 solution on Hardy"
date: 2009-04-15
forum: Desktop Environments
---

### Post by DJonsson2008 on 2009-04-15
Attempting to install Nvidia drivers for my 8400 GS has been a 
nightmarish time sink. Admittedly I'm a noobie, and can rack up
the hours and getting familiar with rollback, install, command
line workouts and navigation --- but what I've ended up with is VESA/Generic drivers for LCD monitor and video card.

I'm not grousing Windows can be a bear in this area as well sometimes,
still I'd like to get some basic Nvidia driver work on this machine.

What I've tried so far...

1. Restricted drivers.
2. EnvyNG
3. Nvidia "official" 180 drivers using the sh Nvidia...run method.

Procedures 2 and 3 seem to be destructive procedures especially when uninstalling them. Both 2 & 3 when they did work left me with a intermitently garbled log in screen and an unusable display if I could work past the log on screen -- sometimes the drivers worked sometime they did not, needless to say they did not instill confidence.

Methods 2 and 3 completely removed my restricted drivers, making rolling
back to them impossible, I do though remember that there were issues
with the restricted drivers that made me attempt the other methods, I 
would though consider re-installing the restricted drivers for one more
attempt provided this would not be a destructive process. 

When I say destructive process, I've lost my usb sound drivers via these processes, have had to reinstall xbuntu and ubuntu desktop several times,
have had to restore foxfire and desktop settings from backup to recover my menu settings and items...and so on...

All I need is basic refresh rate and aspect ratio settings, I don't use Compiz, I'm not a gamer so something basic that works is fine with me.

So...to boil it all down...what is the most robust and hopefully LTS solution for getting basic Nvidia driver functionality to work on Hardy?

---

### Post by bcschmerker on 2009-04-15
> **DJonsson2008 said:**
> Attempting to install Nvidia drivers for my 8400 GS has been a nightmarish time sink. Admittedly I'm a noobie, and can rack up the hours and getting familiar with rollback, install, command
line workouts and navigation --- but what I've ended up with is VESA/Generic drivers for LCD monitor and video card.

I'm not grousing Windows can be a bear in this area as well sometimes,
still I'd like to get some basic Nvidia driver work on this machine.

What I've tried so far...

1. Restricted drivers.
2. EnvyNG
3. Nvidia "official" 180 drivers using the sh Nvidia...run method....

So...to boil it all down...what is the most robust and hopefully LTS solution for getting basic Nvidia driver functionality to work on Hardy?I ran into the same problem with a different wrinkle.  Having recently upgraded my Everex in the hardware, I tried out the nvidia-glx-new packaged driver on my Elitegroup GeForce6100SM-M V1.0 'board &mdash; and ran smack into uncommanded shutdowns on certain Web pages in Mozilla Firefox 3.0.7 (since updated to 3.0.8) without even unmounts of my system's ext3 hard drive volumes, logouts or anything; it basically acts as though the power just got cut.:mad:  I consider this a critical bug; it forced me back to the VESA driver.  Sorry, would I had a better solution.

---

### Post by bcschmerker on 2009-05-07
> **bcschmerker said:**
> ...Having recently upgraded my Everex in the hardware, I tried out the nvidia-glx-new packaged driver on my Elitegroup GeForce6100SM-M V1.0 'board &mdash; and ran smack into uncommanded shutdowns on certain Web pages in Mozilla Firefox...without even unmounts of my system's ext3 hard drive volumes, logouts or anything; it basically acts as though the power just got cut.:mad:  I consider this a critical bug; it forced me back to the VESA driver....Update:  I stumbled upon a fix for the uncommanded shutdowns in my system's local BIOS settings.  Offline burn-in testing of my Everex' new ECS 'board exposed the problems in my main memory, which didn't want to run above a 401 MHz clock.  Although the memory was officially rated as DDR2-800 by its manufacturer, I derated it to DDR2-667 in order to achieve satisfactory stability even with the CPU clock cranked up to 207 MHZ with a x14 multiplier and Vdd=1.275V (as the CPU clock affects the memory clock).  My working BIOS Settings have the CPU clocked to 201 MHz x14.

Does a similar derate of memory speed to stay within demonstrated performance help in your case?

Addendum:  I stand corrected; the uncommanded shutdowns still occur.  67GTA found a firmware explanation for the problem:  Defective (sabotaged?) DSDT's are suspect in both uncommanded-shutdown cases such as mine, and in thermal-management malfunctions reported by laptop users.  Details are at [The DSDT thread](http://ubuntuforums.org/showthread.php?t=1147474) in the [Hardware and Laptops](http://ubuntuforums.org/forumdisplay.php?f=332) category.

---

