---
title: "Desktop sluggish-ness related to Nvidia, common?"
date: 2006-05-16
forum: Desktop Environments
---

### Post by Rtsbasic on 2006-05-16
Hi all, just getting back into Ubuntu, I have an almost vanilla install with the Nvidia drivers installed (system is AMD3000XP, NV6600GT AGP, 1GB RAM, KT400 chipset). First the drivers would not work - trying to load X with the nvidia drivers resulted in a black screen, I overcome this by passing the "nv_disable_pat=1" line to the module, now it loads and works fine.

First of all, does anyone know more specifically what this option does? I think its related to the AGP but I'm not sure. Seems like the black screen problem I had is semi-common on 6600GT AGP cards, maybe because its a PCI-E card with an AGP bridge..:-k 

But moving onto my problem, the desktop feels pretty sluggish to use. Stuff doesn't seem to refresh or draw instantly. I have enabled the render accel option in the xorg config, it helped, but it still feels sluggish. Last time I was using Linux much was when the 2.6 kernel was still fairly new and experimental. Since then my system has been majorly upgraded including a switch from ATI to Nvidia, and it feels like its slowed down? ](*,)  Any suggestions to speed it up a bit would be appreciated.

Cheers.

---

### Post by tseliot on 2006-05-16
Try the latest driver. Have a look at my guide:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")

---

### Post by Rtsbasic on 2006-05-16
I currently have driver 7667, do you think I would see increased 2D performance with a later one? I've just been testing some Quake 3, timedemo 1 at max settings and 1024x768x32 gets an average of 185fps, would seems reasonable as apparently the option I've had to use to make it work decreases performance.

One other odd thing, is the Nvidia settings app, and the Xorg log both reckon my card is PCI-E in some places. This I can accept because it uses a bridge for AGP. But they also say its a Geforce 6600 Go. May just be me, but I didn't know you could even buy that for a desktop? Bit strange.

Edit: Just to say I've updated to a 686 kernel (2.6.12-10-686), still feels sluggish. Espically when changing between tabs on Firefox. Any suggestions on fixing this would be appreciated.

---

### Post by 23meg on 2006-05-16
I'm using a laptop with a 64MB Geforce Go6200 (PCI-E) and I've had sluggish 2D performance with all drivers from 7667 to the current one as well. > I overcome this by passing the "nv_disable_pat=1" line to the module,How exactly do you do this?

---

### Post by Rtsbasic on 2006-05-16
[QUOTE=23meg]I'm using a laptop with a 64MB Geforce Go6200 (PCI-E) and I've had sluggish 2D performance with all drivers from 7667 to the current one as well. How exactly do you do this?[/QUOTE]

Just to clarify, passing that option made X load instead of giving me a black screen, it didn't positively affect performance. I inserted it into /etc/enviroment.

---

### Post by 23meg on 2006-05-16
I know but some similar tweaks were suggested to me at some point (I think on the nvnews.net forums, which you should also check out if you haven't) and I desperately try everything out and see if they improve the situation. Up to now nothing has.

You should also experiment with the NvAGP option in your xorg.conf; refer to the Nvidia readme file for details.

---

### Post by Rtsbasic on 2006-05-16
Thanks for the suggestions - I will have a play around with the AGP settings. One strange thing I noticed is my system reckons AGP is disabled, and yet, I have via_agp & agpgart modules loaded and in use by the Nvidia driver. I will try Nvidia's AGP instead of agpgart.

I've also tried switching to KDE - same lag, and unsuprisingly the same average FPS in quake3 - 184.7fps for the timedemo1.

[QUOTE=23meg]I know but some similar tweaks were suggested to me at some point (I think on the nvnews.net forums, which you should also check out if you haven't) and I desperately try everything out and see if they improve the situation. Up to now nothing has.

You should also experiment with the NvAGP option in your xorg.conf; refer to the Nvidia readme file for details.[/QUOTE]

---

### Post by tseliot on 2006-05-16
[QUOTE=23meg]You should also experiment with the NvAGP option in your xorg.conf; refer to the Nvidia readme file for details.[/QUOTE]
Perhaps adding of these lines to the Section Device of his xorg.conf:
```
Option "NvAgp" "0"
Option "NvAgp" "1"
Option "NvAgp" "2"
Option "NvAGP" "3"
```

Explanation:
Option "NvAgp" "1"  ... use NVAGP, if possible
Option "NvAgp" "2"  ... use AGPGART, if possible
Option "NvAGP" "3"  ... try AGPGART; if that fails, try NVAGP

Use ONLY 1 line per time.

---

### Post by Rtsbasic on 2006-05-16
I'm now running on NVAGP instead of Agpgart, everything works fine - Quake 3 is up by an average of 2FPS as well, but it still feels sluggish to operate. Another example is when a new full screen window is drawn, it doesn't all appear at once, it sorta appears to display in blocks. Scrolling in applications feels like it lags slightly as well.

I'm pretty sure now its nothing to do with the video drivers, unless there are any other tweaks/options I could try. Maybe now its time to start looking at Xorg, is there anything I can adjust or disable to reduce any possible latency at that layer?

Thanks for the suggestions so far guys, its appreciated.

---

### Post by Senesence on 2006-07-27
I have the same exact problem.

Does anyone know a how to speed up the desktop. It's really sluggish.

---

### Post by darkchron on 2006-07-28
Same here, my windows are laggy.. i have reinstalled ubuntu dapper, and now it is laggy.. the one i had on my other disk worked perfectly.. :(

---

