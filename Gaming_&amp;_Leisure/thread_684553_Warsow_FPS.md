---
title: "Warsow FPS?"
date: 2008-02-01
forum: Gaming &amp; Leisure
---

### Post by dfnkt on 2008-02-01
I was having an issue running Warsow, I kept getting "Your opengl installation doesn't support direct rendering" so I fixed that by uninstalling xserver-xgl and now I can play warsow ok but the frames per second isnt that great.

My question is, I have a Geforce2 MX AGP card, currently using the proprietary driver (its listed in the restricted drivers manager as enabled). My fps is around 60 by myself but on some maps can be as low as 30. My max fps I upped to 200 just to test it (default is 90). I know there are some client and game tweaks I can do such as making sure bloom and decals are off to improve my FPS but my worry is that the video card and/or its driver are improperly configured to give me the best FPS. How can I check do make sure that I am using the correct driver and also where can I do a test on the card to see if it is functioning the best it can?

I am sort of new to linux in general so I might need clearer instructions. I would post my xorg.conf but my PC is at home, I am currently at work. 

Thanks all

---

### Post by Mikey_MW on 2008-02-09
I can't say much on the OpenGL problem, but those frame rates seem about right. I used to have a Geforce 2MX and I'd get a little bit more FPS, but then again the rest of the computer was much faster than you'd expect.

---

### Post by FrozenFox on 2008-02-10
How can I check do make sure that I am using the correct driver and also where can I do a test on the card to see if it is functioning the best it can?

^

You can check that your driver is working properly by opening up the console / konsole / terminal (in normal ubuntu i think its under start-->accessories?) and typing glxinfo | grep direct. This will run the program glxinfo, which gives info about your video card drivers n hardware n such, and then reports back the line(s) from the glxinfo output that contain the word "direct", which will tell you if direct rendering is working correctly. If so, open up synaptic (under administration of the start deal) and search for fglrx. You can find the installed version of your fglrx driver from there. Compare that to the newest version for linux you find on the ati/amd site, and see if you are indeed up to date or close to it.

I use nvidia, but I remember someone saying that running "fglrx" in the console/konsole/terminal is useful to see as well, so you might want to take a look at that and see what happens, if anything. Take this last piece of advice with a grain of salt :)

---

