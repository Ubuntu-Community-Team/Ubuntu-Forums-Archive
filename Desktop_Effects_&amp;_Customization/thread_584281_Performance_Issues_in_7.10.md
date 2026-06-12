---
title: "Performance Issues in 7.10"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by therealknewman on 2007-10-20
Hello all! I have been a lurker at these forums for a little while (since 6.10) and have always been able to easily find the answers I need until now. I did a fresh install of Gibbon last night and have started setting everything the way I want it. I installed xgl and enabled restricted video drivers for my radeon x1600pro. All the Compiz features work but the performance is lackluster, much worse than what I had going in 7.04. I have trouble scrolling through websites in firefox, expo and the desktop cube both skip. Pretty much all the stuff I had running well before is lagging on the same system. Have the system requirements been upped in 7.10, or could I have done something wrong in my installation? Would it matter that I installed xgl before enabling the restricted driver? Any help is appreciated by this linux noob.

sys specs:
AMD 3800
1 gb ram
radeon x1600pro
anything else?

---

### Post by 1337455 10534 on 2007-10-21
Ahh, last time I had an AMD, my motherboard got fried after a year of light use... Oh well. Try disabling lm-sensors or Bluetooth (Pref-Admin-Services)...

This won't help, but do
```

sudo apt-get autoremove
sudo apt-get clean

```
in the terminal.
Failing that, just update.
```

sudo apt-get update
sudp apt-get upgrade

```

---

### Post by kozmoracer on 2007-10-21
I also have he same problem - I'm running a x1600pro on a fresh install of gusty... and the best way to describe it would be as 'sluggish'.

Everything in compiz works... but not nicely.

I'm very new to ubuntu, so I don't have much knowledge of anything... but just out of interest you may want to try the following in your terminal.
```
glxinfo | grep "direct rendering"
```

My result is
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

I've been running  around in circles for the last two days trying to find out what I can do to make compiz run a bit smoother... but to no avail.

I'll round up some interesting links that I've found over the past couple of days....

---

### Post by 1337455 10534 on 2007-10-21
> 
I've been running around in circles for the last two days trying to find out what I can do to make compiz run a bit smoother... but to no avail.

I'll round up some interesting links that I've found over the past couple of days....

Please do.. Try some different drivers..
Goto Pref->Screensaver and test out "plasma"

If it runs smoothly, Fusion has no right to be sluggish and you have a fixable problem on your hands. If not, again, try diff drivers... Or buy a P4 HP Pav (wat I have, and at least it runs :lolflag:).

---

