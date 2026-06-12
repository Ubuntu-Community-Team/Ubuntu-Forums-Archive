---
title: "Dell D810, Ubuntu 7.10 - 2nd monitor setup???"
date: 2008-01-07
forum: Dell  Ubuntu Support
---

### Post by tjwolf on 2008-01-07
Hi,
I'm writing this out of desparation: a year or so, I installed Fedora 5 on this Dell Latitude D810 and somehow managed to set it up to support a second screen (a Dell 2007FP connected through the docking station).  The notebook's resolution is 1680x1050 and the external monitor's is 1600x1200 and I had it setup so that the built-in was the "default" and the 2007FP was to the left to form a desktop that included both.  It worked beautifully.

Then, I decided to install Ubuntu 7.10 and forgot to save my config file.  I don't know what I was thinking :(

Ubuntu (and all the auto-updates) installed fine.  But I was looking  at the same thing (more or less) on both screens :(  I figured, since Ubuntu originally offered to install the restricted ATI drivers, I should take it up on its offer - maybe that'll make a difference....nope.

Since I know next to nothing about X config files, I figured that Ubuntu's snazzy **System->Administration->Screens & Graphics** GUI could help me through this...but, boy, was I wrong!  That app has to be the buggiest thing in Ubuntu - I clicked on **Screen 2** and set it to the appropriate monitor and resolution and selected the radio button ** Secondary screen** and added "Extend default screen to the left" and hit OK.  The system told me that it needed a restart for changes to take effect....only problem is that after the restart, now Ubuntu starts in 800x600 mode and asks me whether I want to reconfigure!!!  When I do, it goes back into the System->Administration->Screen & Graphics program and I notice that now the graphics card driver changed from fglrx to some generic vesa driver and there seems to be no way for me to get back to my original configuration...since I was stupid again and didn't bother to save my original X config, I ended up re-installing Ubuntu....that's where I am now.

I know I'm not the brightest bulb in the basket, so can someone just give me the step-by-step instructions on how to get setup properly using the config files?  Obviously, the GUI doesn't seem to be working right for me (or is it user error?  Should I have double-clicked on screen 2 for it to not f#ck with the screen 1 settings??)

Any help is very much appreciated.
tom

---

### Post by lainen on 2008-02-08
I'm having the exact same problem but with a Dell Latitude D630 with an Intel GMA965 Graphics Chipset. After installation the resolution was fine but after i tried to get an image to the secondary screen it bugged out and now i can only use a generic vesa driver and 800x600 resolution.

With regards
Lainen

---

