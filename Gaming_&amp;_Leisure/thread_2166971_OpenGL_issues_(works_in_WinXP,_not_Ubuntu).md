---
title: "OpenGL issues (works in WinXP, not Ubuntu)"
date: 2013-08-11
forum: Gaming &amp; Leisure
---

### Post by Petro Dawg on 2013-08-11
I like running emulators to play my old games, but I'm curious why everything related to OpenGL seems to fail on my computer using Ubuntu 12.04 (also occurred on Xubuntu 12.10).

When ever I try to run something in OpenGL mode I get the following error...

Example Input...
```

zsnes -v 9
```

Output...
```

...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```


This holds true for every SNES, N64, or PSX emulator I've tried (as well as several other 3D programs I've tried from the repos.)  I also think that I can not run standard Ubuntu because of this issue (I end up being logged into Ubuntu2D).

So far I've only been able to get zsnes to run using 512X448 resolution with no OpenGL.

My hardware isn't great (its not a gaming rig) but the same emulators will run with OpenGL on my WinXP hard-drive (I dual-boot across 2 hard-drives).

I'm running a Pentium4 2.8Ghz, 2G RAM, and Integrated Intel Extreme Graphics 2.  There doesn't appear to be any additional drivers for my system.

So is there a fix for this, or am I stuck having to boot into windows to play games from the 90's?  I can live with that solution, but I'd rather not if it can be helped.

---

### Post by SweetAurora on 2013-08-11
That graphics chip is old. Most Linux Games today, including emulators use OpenGL 2.0 and higher. That chip uses OpenGL 1.3 according to Intel. So that's why they won't run. If your PC has an available AGP or PCI slot, look for a used graphics card that supports OpenGL 2.0 or better.

---

### Post by Petro Dawg on 2013-08-11
> **kitsuneinari78 said:**
> That graphics chip is old. Most Linux Games today, including emulators use OpenGL 2.0 and higher. That chip uses OpenGL 1.3 according to Intel. So that's why they won't run. If your PC has an available AGP or PCI slot, look for a used graphics card that supports OpenGL 2.0 or better.

Thanks for the info.  I think I'll just save up for a newer system instead of trying to keep this one alive indefinitely. Upgrading to the graphics card would require an upgrade in power supply as well.  I can live with booting in to windows from time to time for now.

---

### Post by Yellow Pasque on 2013-08-12
```
BadAlloc (insufficient resources for operation)
```
If you have an option in the BIOS to increase video RAM, try to max it out.

---

### Post by DarkAmbient on 2013-08-12
> **Petro Dawg said:**
> 
So far I've only been able to get zsnes to run using 512X448 resolution with no OpenGL.

Can't help you with your problem. Just wanted to add that 512x448 is the native resolution for a snes, isn't that and (if possible) fullscreen mode sufficient? Or does it lag running in "software-rendering"?

---

### Post by Petro Dawg on 2013-08-12
> **DarkAmbient said:**
> Can't help you with your problem. Just wanted to add that 512x448 is the native resolution for a snes, isn't that and (if possible) fullscreen mode sufficient? Or does it lag running in "software-rendering"?

That resolution would be fine in full screen, if I didn't have a widescreen monitor.  Also, for some reason in Ubuntu my desktop doesn't return to the correct resolution after exiting from full screen mode (which is also a bit annoying).  

**@ Temüjin **

I thought I checked that at one point, but I will recheck tonight and see if my BIOS allows more video RAM.  

Thanks for the suggestions.

---

### Post by DarkAmbient on 2013-08-12
You could start the emulator (or whatever app) in fullscreen, through a script where you restore your resolution manually after the app is done. This is untested but I think it should work.

zsnes -v 9
xrandr -s "1920x1080" <- REPLACE WITH YOUR RESOLUTION

Add it to a new empty textfile, save it as .zsnes.sh in your homefolder
Then open yet another empty textfile and paste:

[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=ZSnes
Exec=sh /home/USERNAME/.zsnes.sh
Icon=zsnes (OR PATH TO CUSTOM PNG-IMAGE)

Replace the capital text with whatever needed then save it to **.local/share/applications** named **zsnes_xrandr.desktop**
Now you should find zsnes in the Unity-dash, and it should restore your resolution after you've runned it.


As said it's untested.. and also just a suggestion, I was forced to do something similary running Neverwinter Nights 1 a while ago.

---

### Post by Petro Dawg on 2013-09-23
Well the issue is truly solved now.  I ended up with another free computer with a slower processor (went from Pentium4 2.8GHz to AMD64 1GHz), but I now have Nvidia integrated graphics on the mother board.  Even with the slower processor, things seem to work much better with the newer graphics chip.  I don't really notice a drastic performance drop, and I can now run OpenGL applications without a problem.  I still use Ubuntu2D because its a bit faster than the standard Ubuntu on my system, but I can finally run my emulators (without using Windows), and games like OpenArena without any issue at all.

I must admit, it feels good ditching Windows 100% and doing a total Ubuntu install.   

Still unsure if I want to invest $30 for an upgrade to a used AMD X2 Dual Core chip, things seem to work well enough now, but I expect I'll have to upgrade when the next Ubuntu LTS version comes out.  Hopefully, I'll be able to afford a real computer by then ;).

---

