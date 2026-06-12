---
title: "why wont gnome follow what's in xorg.conf ?"
date: 2007-07-24
forum: Desktop Environments
---

### Post by jdonat on 2007-07-24
this SHOULD be very simple, I write in xorg.conf that I want 1600x1200 @ 70 Hz, and the x server gives me that. done.

But not in  ubuntu-land , oh no , here the maximum freq is bloody 50Hz no mater what ! 
on my Kubuntu partition I can set the monitor model to ctx vl950 and it figures out the usable frequencies right the first time, but in gnome not only can you not choose what model of monitor you have, but when you use gconf-editor to tell it 1600x1200 70Hz it ignores that too!  and dpkg-reconfigure?  I tell it the frequency settings, but it's too damn stupid to figure out what to do with those. 

seriously, what the ****? 

all I want is to use my monitor at the proper resolution and refresh rate, why does ubuntu think it knows better than me?

---

### Post by mcduck on 2007-07-24
> **jdonat said:**
> this SHOULD be very simple, I write in xorg.conf that I want 1600x1200 @ 70 Hz, and the x server gives me that. done.

But not in  ubuntu-land , oh no , here the maximum freq is bloody 50Hz no mater what ! 
on my Kubuntu partition I can set the monitor model to ctx vl950 and it figures out the usable frequencies right the first time, but in gnome not only can you not choose what model of monitor you have, but when you use gconf-editor to tell it 1600x1200 70Hz it ignores that too!  and dpkg-reconfigure?  I tell it the frequency settings, but it's too damn stupid to figure out what to do with those. 

seriously, what the ****? 

all I want is to use my monitor at the proper resolution and refresh rate, why does ubuntu think it knows better than me?

Do you have correct horizontal sync and vertical refresh values in your xorg.conf? If not, that could be the reason why your resolution doesn't work correctly.

---

### Post by mannheim on 2007-07-24
You don't say what video card you are using, but one thing to be aware of is that, with nvidia cards and the nvidia driver, the gnome preferences applet at System->Preferences->Screen Resolution simply reports incorrect information. In my case, it reports that my refresh rate is 50 Hz. In fact, my refresh rate is 75 Hz. You can get the correct information from the nvidia-settings application.

Of course, none of this may apply to you, but I spent a long time wondering once why my refresh rate was "50 Hz", when in fact it wasn't. On your CRT, I guess the flicker at 50 Hz is something dreadful.

---

### Post by jdonat on 2007-07-24
yeah, I changed it there too, didn't seem to do anything, but after a reboot it seems that at least one of those things did the trick.

but dear god, why is it so hard to get all of these things to agree with each other.

---

### Post by RAOF on 2007-07-25
Blame your crappy nVidia drivers.  They deliberately misrepresent the refresh rate to be 50Hz regardless of what the actual refresh rate is.

Actually, it's used in TwinView.  You'll tend to find that the 1st screen gets 50Hz, the second gets 51Hz, etc.

---

### Post by stibbons31 on 2007-11-05
I do have exactly the same problem, with indeed the nvidia driver. This driver should report bad screen name/supported frequency/what ever. The screen behaviour is always the same:
1) I set up the only Horizontal + Fretical Freq supported by my screen in xorg.conf. 
2) When X starts, it visibily beggins with this very H/V freq, 
3) but suddently switch to the bloody 50 Hz (bad for eyes)

The way I found to have it working to the right freq is to use nvidia-setting after each change in xorg.conf, is the correct freq is available in the display/resolution panel, just select it and make it write to xorg.conf. It's not very confortable, but it works.

Hope this helps

---

