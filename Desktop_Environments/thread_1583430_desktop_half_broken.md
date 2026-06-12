---
title: "desktop half broken"
date: 2010-09-27
forum: Desktop Environments
---

### Post by RasterBurn on 2010-09-27
hey everyone, i am having some issues with my install, they popped up the day after the most recent fglrx updates, can somebody help me? i am not sure what information you all need but anyways, to start it out, i use 2 ATI Sapphire HD 3870 cards, I have been using the video drivers from the ati site as they are the only ones that work with 3d apps on my computer i use the 1280 x 720 resolution (my computer is hooked up to the tv via HDMI) this was working perfectly, I had an update for the fglrx and installed them, rebooted, and it nocked out the 3d applications so i reinstalled the ati drivers again to get things working properly, anyways, i booted up the next day to get an error saying "nmbd already running" and then some graphics error and had to boot into low resolution mode or something like that, and to return the desktop close to normal i had to delete xorg.conf and reboot to give the desktop resolutions back, unfortunatly 1024 x 768 looks washed out and 1280 x 720 expands past the edges of the tv thus not being able to see the menu bars, after having said that, none of the 3d apps that i use will load with the failsafe driver, if i try to enable the fglrx driver i am back to deleting xorg.conf and if i re-install the ati driver i get the same problem, can someone please help me, just let me know what log information i need to supply

also i am using th 64bit Ubuntu 9.10

---

### Post by RasterBurn on 2010-09-29
bump

---

### Post by Dustin2128 on 2010-09-29
> **RasterBurn said:**
> hey everyone, i am having some issues with my install, they popped up the day after the most recent fglrx updates, can somebody help me? i am not sure what information you all need but anyways, to start it out, i use 2 ATI Sapphire HD 3870 cards, I have been using the video drivers from the ati site as they are the only ones that work with 3d apps on my computer i use the 1280 x 720 resolution (my computer is hooked up to the tv via HDMI) this was working perfectly, I had an update for the fglrx and installed them, rebooted, and it nocked out the 3d applications so i reinstalled the ati drivers again to get things working properly, anyways, i booted up the next day to get an error saying "nmbd already running" and then some graphics error and had to boot into low resolution mode or something like that, and to return the desktop close to normal i had to delete xorg.conf and reboot to give the desktop resolutions back, unfortunatly 1024 x 768 looks washed out and 1280 x 720 expands past the edges of the tv thus not being able to see the menu bars, after having said that, none of the 3d apps that i use will load with the failsafe driver, if i try to enable the fglrx driver i am back to deleting xorg.conf and if i re-install the ati driver i get the same problem, can someone please help me, just let me know what log information i need to supply

also i am using th 64bit Ubuntu 9.10
every other radeon update seems to break something :(
what's it like without the proprietary driver?

---

### Post by TBABill on 2010-09-29
Many threads and posts today about the recent updates borking systems, but followed by responses with "I installed xxx driver from xxx site" instead of installing via the repositories. Obviously some people need those newer driver capabilities but when the kernel is updated I imagine the video drivers need to be reinstalled. The system cannot know an outside source was installed into the system so breakages are likely to occur. 

Maybe revert to the open source driver so you can retrace your steps to reinstall the appropriate drivers and dependencies? And a package request for the updated driver?

---

### Post by RasterBurn on 2010-09-30
so the issue with mine is, without the fglrx driver (i think i put the letters right) the best resolution i can do is 1024x768 and it doesnt look right on my 42" widescreen HD tv the picture quality is pretty washed out and faded, the 3D rendering apps i use well, either they dont fire up or they are in an un-usable state, if i go to use my normal resolution (1280 x 720) the menu and task bars extend past the borders of the screen (cant click on menus cause i cant see them) and also my audio doesnt work (its set up to run through the graphics cards and to the tv via HDMI).

haveing said that, you know why the ati drivers from the ati site are so important, the updates that i had installed were directly from the repository via the update manager, this driver doesnt quite cut it for doing 3D rendering.

If i install the proprietary drivers from the repository (already installed but failing) and it creates the xorg.conf file (i had to delete it to get things somewhat working again) then i can no longer boot into the desktop normally, I end up getting a few errors and being forced to boot into low resolution mode untill i delete the xorg.conf file thus returning back to square one.

I have also tried re-installing the ATI drivers for the card from their site with the same results

---

### Post by RasterBurn on 2010-09-30
ok so i have nothing but good news of the day, today i sorted out the issues with my graphics drivers, turns out that the fglrx drivers from the repository are causeing issues, i uninstalled them (including purging config files), rebooted and proceeded to install the ATI Catalyst drivers version 10.9 of course reboot and wonder why nothing was working but the 720 resolution.... turns out i forgot to enable to drivers, head to device drivers and enable them, reboot and yay, all is working again :)

---

