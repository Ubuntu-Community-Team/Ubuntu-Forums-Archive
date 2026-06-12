---
title: "xfwm compositing really slow compared to compiz in GNOME"
date: 2007-07-07
forum: Desktop Environments
---

### Post by hotani on 2007-07-07
I just set up an old Dell Latitude D600 laptop yesterday, and if you are familiar with this machine you'll know it isn't exactly the fastest horse in the race. Since I've been toying with Xfce recently, and I love xfwm and its compositor as it has just the right amount of bling and functionality for my tastes, this is what I put on the laptop.

It was DOG SLOW. Xfce ran fine without the compositor turned on, but as soon as I checked that box, moving windows around became a chore. Especially the terminal window--without transparency.

So as an experiment, I installed 'ubuntu-desktop' and logged into GNOME. I turned on desktop effects (compiz), and it was reasonably fast. Granted, it is nowhere near my desktop's nVidia 7600 GT performance, but it was very workable. Even something I consider to be pretty intensive like rotating the cube was handled well.

Why such a big difference between the two? I think of compiz as doing too much, while as I mentioned above, the xfwm compositing is very mild: some basic shadows and transparency--just the right amount of bling to not get in the way. Yet compiz is so much faster.

I have noticed poor performance on my work desktop as well when I have several windows open in Xfce using compositing. When I alt-tab to an app on a different desktop when several windows are open, it seems to get bogged down. I never had this issue with compiz (or beryl).

The video card on the laptop is an ATI Radeon 9000.

---

### Post by LuisAugusto on 2007-07-07
Because compiz is actually replacing metacity, in XFCE you're repainting everything twice (it probably uses xcompmgr or some fork as KDE's kompmgr)

---

### Post by cheemosabe on 2008-01-13
Was having the same problem. xfwm uses EXA acceleration method for compositing. I added the following to the Devices section in my xorg.conf and it solved it:

        Option "AccelMethod" "EXA"

---

### Post by new2*buntu on 2008-02-02
I have noticed that moving the terminal window around is slow with compositing turned on, and if there is transparency during window move it makes everything that slow. But I still love the compositor. I just use it for shadows and transparency of popup windows and window decorations. Also, I tend to not move the terminal around.

---

