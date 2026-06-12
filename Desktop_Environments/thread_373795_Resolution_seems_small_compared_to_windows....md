---
title: "Resolution seems small compared to windows..."
date: 2007-03-01
forum: Desktop Environments
---

### Post by Skeorx13 on 2007-03-01
I recently dualbooted WinXP and Ubuntu 6.10 and have set up the resolutions of my screens to the same as they are set to my windows partition. For some reason the icons in windows look way smaller than in linux. Is there an option to shrink down the icons in Ubuntu to clear up some desktop space? Even with applications open the desktop seems small and I can never seem to get the amount of space to maneuver that I have in XP. Firefox, amarok, basic menus, and such all seem overly zoomed in to me. I'm in 1280x1024 on my main 19" monitor and it feels like I'm in 800x600 (my second 15" monitor is in 1024x1024 - also a problem since its max resolution is 1024x768, but I posted that one in another thread). Does anyone know of any tricks to help me out?

---

### Post by Nikron on 2007-03-01
If you want to make your icons on your  desktop to be smaller, just right click them and click stretch icon..  If you want the icons on the panels to be smaller, right click the panels and make them smaller in prosperities.

---

### Post by airtonix on 2007-03-01
this is becuase winxp icons only have three sizes.....

where as png and svg....they scale depending on your res and like Nikron says....you can strecth...or shrink them. bit confusing in that to shrink some icon you must first select strecth.

bit like winsod where to "stop" the computer you must first select the "start" button. lol:lolflag:

---

### Post by Skeorx13 on 2007-03-01
I'm on my XP computer at work right now, but I'll try this when I get home. Question though, when you select stretch does it automatically adjust the icons for the set resolution? or do you have to specify a length and width (in pixels for example)? or do you adjust their sizes using the mouse cursor (like when resizing firefox windows)?

Edit: 
Yup that did the trick. I have to resize every single icon by hand, which you didn't have to do in windows, but I can see where this has its advantages. Being able to make certain icons small and others you actually want to have larger. I also figured out how to move my lower taskbar and move things around on the taskbars. This is much better now. Thanks all!

---

### Post by RandomJoe on 2007-03-02
My Dell laptop has a 1600x1200 LCD that's only 15" in size.  When X would start, it grabbed the physical size of the panel from the EDID data and upscaled everything to hit a physical size constraint.  (Not sure what that target was, or why...)  I can see (and like) tiny fonts and such, so wanted a large desktop instead.  I added a line to the xorg.conf file to override the display-reported screen size.

In the Monitor section, add:
```
DisplaySize 388 291
```
The sizes are width and height in millimeters.  This line told X that my laptop's screen was "really" roughly 15" x 11" instead of the actual 12" x 9".  Which then reduced the size of everything nicely.

Be sure to keep the numbers in the proper proportions for your screen (4:3, 16:9, whatever).

I'm not sure just how far you can take this - even if it does keep scaling things down, eventually you'll have too few pixels being used for each element and things will look bad.

---

