---
title: "ubuntu 10.10 - X server/Gnome randomly crashing on startup"
date: 2012-01-19
forum: Desktop Environments
---

### Post by ste1985 on 2012-01-19
Hi guys

I've recently installed ubuntu 10.10 on an old laptop (toshiba satellite pro m40, 1.4ghz celeron processor 512mb ram radeon mobility 200m) and I am having some problems with Xserver/Gnome randomly crashing on startup. I am dual booting windows 7 starter and ubuntu.

When I boot into ubuntu I always get to the graphical login prompt, the problem is that when i click on my username and type in my password sometimes I will be logged in fine and the gnome desktop will appear and I will be able to use the system as normal, but sometimes (more often than not) after i type my password I will get stuck at the login screen and not be able to go any further (just the wallpaper and the mouse pointer will be shown, nothing else). When this happens I am always able to hit ctrl + alt +f1 to get to a command prompt so that I can reboot the system, usually after I reboot the laptop a couple of times I can log in properly and have a working system but as you can imagine this gets a bit annoying after a while!

I have done a lot of searching on google and on various forums about this problem and lots of people have said that it could be a graphics driver issue and to update the driver, however, these posts all seem to relate to computers with nvidia graphics cards and mine is ATI. I have looked on the ATI website for newer drivers but I cant find any for my chipset. I have looked at Xorg.o.log and it shows that the driver it's loading is compatible with my chipset so I've got no idea what could be wrong. If anybody has got any ideas what might be causing the problem I'd be gratefull. Btw, my Xserver version is 1.9.0 if it helps.

cheers

---

### Post by sgiannerini on 2012-01-21
I have the same problem, namely, a Toshiba Laptop Satellite Pro M40 with celeron 1.4 and ATI M200 on which i have installed Ubuntu 11.10.

After I login successfully, sometimes I am left with a blank screen with just the mouse pointer and the only way to escape from this is to ctrl-alt-F1 login and reboot.

I have noticed that if I login as guest after the reboot then everything is ok.

I also mention that my ATI M200 video card is not recognized by the system, maybe try with ATI proprietary drivers but a lot of people is complaning about these drivers.

Ciao

Simone

---

