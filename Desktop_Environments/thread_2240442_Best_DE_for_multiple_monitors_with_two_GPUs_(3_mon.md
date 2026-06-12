---
title: "Best DE for multiple monitors with two GPUs (3 monitors) in 2014?"
date: 2014-08-20
forum: Desktop Environments
---

### Post by AnttiV on 2014-08-20
Hi! I searched around and found a couple of posts, but they were from anywhere between 2007 and 2013 (and most of them just deal with dual-monitors). But things change quickly in this field, as we all know.

So, what is the state of having multiple monitors on linux in 2014? I honestly didn't think it would be a problem at all, since Win & Mac do it just perfectly. I expected perhaps a little fiddling with configs or such, not this kind of "thou shall not enable xinerama, lest Unity gets its knickers in a twist and quite the job". :)

Anyway, my machine is a ThinkCentre M55 (C2D E6600 @ 2.40GHz, 4Gb RAM) with two nVidia cards: GeForce GT240 (primary) and Quadro NVS 290 (two monitors).
The goal is to have an extended desktop that I can drag windows around in, preferably with some kind of acceleration (so it's fast and snappy, but I don't need any fancy effects.) This machine will not be used for any gaming, so optimizing for that is not needed. I currently have installed/tried ubuntu and kubuntu on it, but will probably start from scratch anyway so if there's a whole distro with the best DE for this already, I'd be willing to go for that. (But prefer a Debian-based distro, so will probably just install DE to debian/*buntu distro.) 

If possible, I'd prefer to maximize windows to-monitor, not to-desktop (not a big thing, I don't usually maximize anything, but that's a behavior I'm used to from working with Windows+multimonitor.)

ps. It might be worth to say that I don't need a fully open-source platform, so can install nVidia (and others if needed) proprietary drivers (and I usually do anyway).

---

### Post by Tadaen_Sylvermane on 2014-08-20
I use vanilla ubuntu at the moment even with 2 screens but my preference for multi screens is kde / kubuntu. Built in ability to set different wallpapers. Snap features are to the individual screens, not the whole desktop. Works great with different resolutions. Easy to configure. I have yet to find a downside to kde for that purpose.

xfce while light is difficult at best for multi screens, from last time I tried anyway. Had to have scripts to activate the other monitors and so forth. Unity does it just fine but doesn't give you the ability to choose wallpaper per screen. Don't know anything about lxde or pure window managers.

As far as the snap being to the screen and not the whole desktop I haven't found a window manager that did snap to the entire desktop.

---

### Post by QIII on 2014-08-20
Hello!

Windows and Mac may do it, but it's not anything Microsoft or Apple have done.

OEMs write drivers, not purveyors of OSes.  Linux is an afterthought for them, so if things don't work it's not due to any fault with Linux distributors.

I run three monitors without any problems on single a triple head card right now and have done it on multiple cards -- albeit identical ones.

---

### Post by AnttiV on 2014-08-20
Ah good to know about that snap-to-monitor is the default then.
But yeah, two monitors seem to work everywhere and everytime, at least when they are connected to a single GPU. When you have more than one and/or multiple graphics cards, the excrement tends to hit the fan. I can tell you for a fact, that Unity does NOT work across multiple graphics card out-of-the-box. It MAY work with tinkering, but I don't know what to do and how. If I enable xinerama (to get extended desktop and not just three different X instances) Unity will not launch (nor will anything else really.) I need to drop down to console and delete the xorg.conf (yeah, I could modify, but deleting is easier at this point) to get it to boot into Unity again (and of course disabling xinerama by doing that). Base Mosaic doesn't work across different GPUs (and is not supported on the NVS anyway?)

So I'm left with just questions. "How to do it?" and "What to try?".

But, thanks. I'll try KDE (in either Mint or Kubuntu flavor) the next time I have the chance to tinker with that computer.

EDIT:

> **QIII said:**
> Hello!

Windows and Mac may do it, but it's not anything Microsoft or Apple have done.

OEMs write drivers, not purveyors of OSes. Linux is an afterthought for them, so if things don't work it's not due to any fault with Linux distributors.

I run three monitors without any problems on single a triple head card right now and have done it on multiple cards -- albeit identical ones.

Yeah, monitors connected to a single card seem to work fine. And it is highly likely that identical cards work better than different ones. But on the driver/OS side I find it hard to blame the OEMs for all the problems. Because triple-head across GF240+NVS290 *DOES* work in ubuntu - in techincal terms, as in I get picture and wallpaper on every screen and I can move my mouse anywhere, it's just that Unity doesn't launch. (because xinerama, I gather.) So technically they work, but SOME aspect of the OS always slams its nose on the ground and goes belly-up. I wouldn't necessarily blame the driver-writers at that point, but I'm not a GPU-driver developer by any stretch of the imagination, so I don't really know. It still might be that.

Anyway, what triple-head are you using? Is there a (really cheap) solution that I could purchase to be able to run three monitors easily (or at least easier) on a *buntu distro? Preferable with comparable (or at least no less) power to the GT240/NVS290 combo. Meaning smooth and snappy GUI, but not necessarily any "real" 3D power?

---

### Post by tsteiger on 2014-08-21
I have the same frustration. In 12.04 I had 4 monitors working fine across two different video cards, but I figured I would give Unity a try since I was feeling like I kept putting it off, but there were things that would be nice on it.  There is a demo out there on YouTube of some Unity setup with 8 monitors, but of course no information on how to get that working.  I updated with a clean install to 14.04 in part because I was looking for some of the improvements to Kernel versions and such that I was not getting in the normal release stream with 12.04.

Very frustrating to have a working system go to non-functional because Ubuntu no longer has an option (without installing Gnome-flashback I guess) for running across multiple video cards and displays.  I agree with the OP that this seems crazy in a world where you can just plug systems together with Windows and Mac and all the displays work.  I could put Windows 7 or 8 on this machine right now and have a functional desktop right after install.  Not going to happen because I can't stand Windows, but so sad.

Unity has some really nice aspects to it, but it really needs to get modernized in how it works with X, or X needs to have better multi-head support. I don't understand why support for Xinerama wasn't included since Mir isn't ready for prime time. I guess most people only use 2 monitors so those of us who prefer more real estate are out of luck.

Maybe time to switch distro's or at least dump Unity again in favor of Gnome.

For the record my system has;
  - GEForce GT 520 - with 2 monitors
  - GEForce GT 560 - with 2 monitors

I don't know if this works better with ATI as I've been an nVidia user for so long...

---

### Post by AnttiV on 2014-08-22
I installed Mint 17 KDE, then right after install enabled nVidia proprietary drivers. After a reboot enabled both of the NVS290 screens and switched on xinerama. The, rebooting again, I got a functional triple-head desktop. I can change wallpapers per-monitor and each window maximizes to monitor. I can drag windows between monitors with easy.

This just a tad slow now. I think xinerama disables 3D acceleration? (correct me if I'm wrong, please.) But at least I *can* enable the display and have a functioning desktop, at the same time. Truth to be told, this *is* probably enough for this computer, considering the "work" being done on it, but of course I would *like* to have some sort of acceleration to have snappier experience moving windows and such. But if the choice is between TripleHead OR acceleration, three monitors win hands down. (On this computer, of course. I wouldn't dream on losing 3D on my gaming rig.)

But if anyone knows any tricks, other DEs to try, any work-arounds... please tell. I'm willing to tinker and am not "afraid of the terminal" :) This isn't a production-level computer, so I can (and would probably like to) try some experimental stuff, if there is any. (I've been away from the "linux scene" for a number of years now, so I don't know the latest developments or anything. I think my last full-time linux desktop was running Ubuntu 9.. Possibly Debian 3/4. Before Unity anyway.)

Also, the computer does not currently hold any actual important data, so re-formatting and starting over and trying different things is easy now, if that is required.



ps. Would I have (much) easier time if I purchase a 5xxx/6xxx series ATI card that can do three-monitor eyeFinity or a 650 GeForce with the required connectors to do a triple-head setup? Can the DEs work with three monitors (without xinerama) if they are all connected to one card? (I'd want to steer away from this "solution", since I don't necessarily want to spend any money on that computer, as it isn't in any important use. Also I LIKE tinkering with older hardware :)

Also, if the choice is between "*nix + non-accelerated triplehead" vs "fully-accelerated and snappy triplehead + Windows"... well, I don't like Windows that much, but it IS very hard to find an excuse in that case to run linux on it, because it would be a crippled experience.

---

### Post by Tadaen_Sylvermane on 2014-08-23
> [COLOR=#000000]Also, if the choice is between "*nix + non-accelerated triplehead" vs "fully-accelerated and snappy triplehead + Windows"... well, I don't like Windows that much, but it IS very hard to find an excuse in that case to run linux on it, because it would be a crippled experience.[/COLOR]

In the end whatever gets the job done and you are happy with is the choice to make. Don't make it based on others recommendations. Try them both, if one works better then thats the clear winner. It's very subjective what is better. Although I agree with the statement earlier that multi monitor support isn't a big deal with the virtual desktops but it's all in what you get used to I suppose. I used to be real big on multi screens. But once I got used to virtual desktops, my 2nd monitor is just generating heat. I should leave it off with as little as I've found I need it. Waste of 250 bucks... for me at least. Some workloads though practically require multiple screens, stock trading for one.

---

