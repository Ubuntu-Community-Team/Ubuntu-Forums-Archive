---
title: "Live Gusty?"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by natman on 2007-09-29
I have a laptop, intel core2 nvida go 7200 ( 128 shared ) and 2 gb  ram, i put in a gusty live cd to find out what it looked like and if the dsktop effects would work on my machine,  there is nothing visually different and i went to system - apperance and when i click the advanced ( one with the magic wand icon ) the box fezzez and i have to force a quit on the appereance box.
Does this mean i cant run gusty with all the bells and whistles out of the box? or do i need a full installation to test it out?

---

### Post by Rupertronco on 2007-09-29
I don't think you can draw accurate conclusions on the Live CD, I may be wrong but I wouldn't recommend writing off gutsy because the live cd won't work. 

Did you try enabling the restricted drivers (or install the nvidia-glx package) then restarting X?

---

### Post by FuturePilot on 2007-09-29
You need to install the Nvidia driver. It can be done on the Gutsy live CD. When you boot it and get to the desktop there should be a notification that pops up about restricted drivers. Go and install the Nvidia driver. (It's not installing anything to the hard drive, don't worry ;)) Then just logout and it should automatically restart X and then try the desktop effects. Actually when you come back to the desktop they should already be enabled.

---

### Post by MoebusNet on 2007-10-15
Tried that with my D800 using the restricted driver for the NV Geforce4 Ti 4200 Go AGP 8x video card. Logged out, logged back in and still can't enable desktop effects. System still demands a restart which will, of course, erase everything from memory. Always back to square 1...

---

### Post by FuturePilot on 2007-10-15
If your card has less than 64MB VRAM you won't be able to enable them at all.

---

