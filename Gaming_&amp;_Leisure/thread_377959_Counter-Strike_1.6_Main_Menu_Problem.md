---
title: "Counter-Strike 1.6 Main Menu Problem"
date: 2007-03-06
forum: Gaming &amp; Leisure
---

### Post by u-blunt-2 on 2007-03-06
Howdy !
I stumbled upon linux-games howto installing and running counter-strike 1.6 via WINE. I was surprised this was poissible and very pleased. After folowwing the howto, I could play online (with a little more lag than under winblows). I tried changing the video option to software and D3D. To my dismay, Wine crashed.

After restarting Counter-Strike, I accessed the Main Menu to find that The menu Image was zoomed (as if it were at a much higher resolution) and I cannot see the text options (Tahoma.ttf is installed). When scrolling around with my mouse, I can hear the menu option click sound, but if i click them, wine crashes and I end up at my desktop with 800x600 resolution. 

My wine is properly configured (Oss sound, and the sort). Steam appears to have some trouble (as can be expected with the emulator-like program). I tried uninstalling Steam, erasing the folders and their content, and reinstalling to get the same problem.

Can anyone help ? What can do besides reinstalling and reconfiguring wine ? Is that the only solution ? Wine works fine with other apps.

---

### Post by buttons on 2007-03-10
> **u-blunt-2 said:**
> Howdy !
I stumbled upon linux-games howto installing and running counter-strike 1.6 via WINE. I was surprised this was poissible and very pleased. After folowwing the howto, I could play online (with a little more lag than under winblows). I tried changing the video option to software and D3D. To my dismay, Wine crashed.

After restarting Counter-Strike, I accessed the Main Menu to find that The menu Image was zoomed (as if it were at a much higher resolution) and I cannot see the text options (Tahoma.ttf is installed). When scrolling around with my mouse, I can hear the menu option click sound, but if i click them, wine crashes and I end up at my desktop with 800x600 resolution. 

My wine is properly configured (Oss sound, and the sort). Steam appears to have some trouble (as can be expected with the emulator-like program). I tried uninstalling Steam, erasing the folders and their content, and reinstalling to get the same problem.

Can anyone help ? What can do besides reinstalling and reconfiguring wine ? Is that the only solution ? Wine works fine with other apps.

Do NOT use D3d with CS 1.6.  I probably don't have to tell you that now :P  OpenGL should always be used, whether on windows or linux.  The directx port is buggy.

That said, there USED to be a command line option for selecting the OpenGL engine, which I believe was "-gl".  I just spent a bit of time trying to verify that, but it appears Valve may have gotten rid of this option now that Source is here.  If that doesn't work I'm afraid the best course is to simply blow up your wine install and try it again :(

---

### Post by kylet450 on 2007-03-11
Cool, weres the website?

---

### Post by u-blunt-2 on 2007-03-19
Just google "wine counter-strike" to get the guide.
The -gl option is the way to go. However I ended up reinstalling wine (too impatient, didnt check back on forum!). 

I now have a problem with my keyboard. As soon as I press shift to walk in game, it's as if I have caps lock enabled (which isin't the case). Nothing to do to get rid of it besides restarting Steam.

I will post new thread for this.

---

