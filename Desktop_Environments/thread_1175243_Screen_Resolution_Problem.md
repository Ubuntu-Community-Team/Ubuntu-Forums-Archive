---
title: "Screen Resolution Problem"
date: 2009-05-31
forum: Desktop Environments
---

### Post by nmccrina on 2009-05-31
After an unsuccessful attempt at a dual-monitor setup using an external monitor with my laptop, I'm stuck at a resolution of 1024x768. My laptop's screen resolution should be 1280x800. GNOME figured it out correctly at install, and I've never had a problem with it, but now that it left that resolution I can't figure out how to get back because in System->Preferences->Display there is no 1280x800 option. 
As far as I can remember the steps I took to get into this predicament were:
1. Shutdown the computer, hooked up the external monitor.
2. Started Ubuntu.
3. Both screens worked, but both displays were at 1024x768, which was correct for the external monitor, but incorrect for my laptop monitor.
4. Went into System->Display->Preferences and unchecked the "mirror screens" option.
5. When I hit apply, it said that some setting needed to be changed, and that it could change them for me. I agreed, and entered my password. Now I'm thinking that these settings it changed are probably the ones that are screwing up my display, but I didn't pay attention to where it said these settings were at the time. I can't reproduce the prompt, either. Does someone perhaps know what these settings were that it changed?
6. The screens no longer mirrored each other, but the incorrect resolution on the laptop was bugging me, so I went back into System->Preferences->Display to see if I could change the resolution for individual monitors. I didn't see any way to do this, but the Display menu doesn't have an option for 1280x800 anyway.
7. So I unhooked the external monitor and restarted, to see if GNOME would figure out the correct resolution, but it didn't. It booted up into what seemed like 300x200. I have got it back to 1024x768, but am confused about how to undo whatever I did and get it back to 1280x800.

---

### Post by Scott30101 on 2009-07-23
I'm having the EXACT same problem and its driving me crazy.  Please help!!!!!!!!:confused::(

---

### Post by doublemike on 2009-07-24
I'm in the same boat. Stupid external monitor never worked either.

---

### Post by doublemike on 2009-07-24
I plugged in an external monitor again and I got the 1280x800 resolution to show up again. The happened when I clicked on the external monitor. I chose this resolution and hit apply. I was then prompted by the same popup warning and had to log in to make the change.

Looking at my /etc/X11/xorg.conf  file I see it was updated.


Section "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
  SubSection "Display"
    Virtual 1280 1664
  EndSubSection
EndSection

Section "Device"
  Identifier  "Configured Video Device"
EndSection



The older file that was replace was this:

Section "Device"
  Identifier  "Configured Video Device"
  Option    "UseFBDev"    "true"
EndSection

Section "Monitor"
  Identifier  "Configured Monitor"
EndSection

Section "Screen"
  Identifier  "Default Screen"
  Monitor   "Configured Monitor"
  Device    "Configured Video Device"
EndSection


Hope this helps.

---

### Post by evilpenguin on 2009-08-10
I had a similar problem with the Intel video in my Lenovo Y510. I plugged in a second monitor that had a max resolution of 1024x768 and after using it I found that I could not put my latop screen back to its highest resolution (1280x800). I tried and tried to get it back.

Finally, I moved away my xorg.conf in /etc/X11:

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.limited

And restarted X. Everything was back to normal. I had done finds for all file changed in the last 10 minutes, I had done a disk-wide grep for the string "1024x768" Man, I had looked and looked.

I'm not saying I recommend blowing this file away, but it sure worked for me. (BTW, I did the "mv" so I could put it back if it really horked things up. ALWAYS make sure you can undo your radical changes!)

---

