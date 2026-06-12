---
title: "nvidia redrawing trouble"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by GlennW on 2007-07-23
I hope that I'm somewhat close to being in the right category. Sorry, I'm a newb and trying really hard to follow the posts and the how-to's. The work that you guys do is fantastic.

Here's the issue at hand. I recently purchased an nVidia Geforce 6200 DDR2 TV DVI in order to be compatible with Ubuntu. I followed the how-to's and get everything running okay. Not great but getting there. I have a dual boot with XP Pro. I boot that up and bring up the nVidia config box and there's a place where you can speed up the GPU and the Memory Clock (or something like that). Instead of playing with the sliders, I clicked "Detect Optimal Settings." After it was finished testing, and the numbers were high, I made sure that I didn't click save so that when I rebooted the settings would return to default. Everything was running fine until I did reboot for some completely unrelated reason and before anything was accessible in the desktop the screen was full of artifacts (garbled). I rebooted into safe mode but now can't access that same settings box. I get nVidia's manager and that's as useful as tits on a bull. In safe mode, I accessed the properties to lower the rez which I can move the slider lower but after hitting apply it goes back to 1024 x 768. 

How can I find that setting box to check nVidia's GPU and Memory Clock settings?

Thanks...

---

### Post by Gausian on 2007-07-24
have you tried......

```
sudo nvidia-settings
```

type that into the terminal and see if you can get your settings to save.

---

### Post by GlennW on 2007-07-24
> **Gausian said:**
> have you tried......

```
sudo nvidia-settings
```

type that into the terminal and see if you can get your settings to save.

Yes, that's not the problem. Please see the original post. I guess I should have been more specific. Here goes. There's two issues both stemming from the recent installation of a new nVidia Geforce 6200 AGP 256Mb DDR2 TV DVI. I have a dual boot setup with XP Pro.

1. In Ubuntu, after managing to, after a lot of reading and messing around, get the video settings right. Upon boot up, I had a stable connection, nothing to click to make an internet connection, just to open firefox. Now, however, after about a month, and for some unknown reason, I have to manually connect. 

**[COLOR="Red"]The question:[/COLOR] how do I save the settings so that when I boot up next time my internet connection is open?**

2. In XP, I had opened the nVidia settings box and was going through it since it's slightly different than in Ubuntu and found the sliders for the GPU and Memory Clock. There is a button at the bottom of the box which is labeled "Detect Optimal Settings." I clicked that and after it running through it's testing cycles, reset the sliders quite high. I figured if that's your optimal setting then great. There was a check/uncheck box which allows for these settings to be saved upon the next startup. I did not check that box. Everything ran nice and quick and crisply. Upon the next startup (and you know how long XP takes to get everything running) when I finally had access to the desktop, the screen became garbled. It appears that the nVidia settings are the last instructions loaded during startup. I've booted up in safe mode but can't find/don't have access to the same nVidia settings box only nVidia's desktop manager which doesn't allow setting changes, at least in this current state. I've accessed the properties from the desktop and tried to lower the rez from safe mode's 1024 x 768 to 800 x 600 but the slider keeps popping back up.
[B]
[COLOR="Red"]The question:[/COLOR] how do I access nvidia's settings in XP in safe mode to be able to boot back up in normal mode?[/B]

---

