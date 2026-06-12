---
title: "Flashing in screensavers"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by sufslnd on 2008-03-16
Hi,

This is my first post on this forum, so bear with me ;)

I installed Ubuntu on my laptop and desktop about one week ago, and have not booted windows since. I have googeled everywhere and found answers to all my problems (ATI driver..) and such. However, I have a problem with the screensavers.

When i start a screensaver in preview or fullscreen it flashes. Like I have really bad framerates. If anyone of you have tried taking a picture of a CRT monitor with your mobile cam you know what I mean.

Is this relevant:?
~$ glxgears
40532 frames in 5.0 seconds = 8092.930 FPS
41025 frames in 5.0 seconds = 8191.353 FPS
40223 frames in 5.0 seconds = 8042.314 FPS
39486 frames in 5.0 seconds = 7879.968 FPS
40235 frames in 5.0 seconds = 8032.575 FPS
40897 frames in 5.0 seconds = 8159.925 FPS

And, yes, the glxgears flashes when run from the console (even with 8k FPS??)

Anyone know what this is? I have an ATI card on the issued computer..

Cheers,
Stefan

---

### Post by Ub1476 on 2008-03-16
Which ATI driver are you using? The one downloaded from Restricted Driver (..) or the latest from fglrx driver from ATI (8.3 currently)? Have you tried to disable Compiz and see if it helps?

As you might have understood, there are quite some problems with the ATI driver atm. ATI is working on improving them, though.

---

### Post by sufslnd on 2008-03-16
I think I managed to update to the latest driver, Catalyst 8.3. I then edited some config file to get the fancy effects to work. (Man did i feel leet when I got that to work:P )

I did deactivate compiz as you said, and now the screensaver works perfectly! I would, however, like to use both a smooth screensaver, and the compiz effects. It is for instance really great to use the desktop cube to get an overview. 

Is there a way to do this? I am running an integrated intel card on my laptop (which is pretty cool since it does not handle Vista, and the effects in Compiz kics Vistas ***), and there is no issues whatsoever with neither Compiz nor screensavers. That pretty much underlines that it is a driver problem I guess..

Cheers,
Stefan

---

### Post by Ub1476 on 2008-03-16
Do you use an ATI card with the fglrx/Catalyst drivers or an integrated Intel card?

ATIs driver cannot handle video playback/screensaver yet with Compiz running. It's a very requested feature though, so I guess they'll fix that soon. 

If you are very lucky, Catalyst 8.4 will make it into Hardy Heron/Ubuntu 8.04 in April, with video playback support with Compiz on. If not, Envy can always update the latest driver for you..

---

### Post by sufslnd on 2008-03-16
> **Ub1476 said:**
> Do you use an ATI card with the fglrx/Catalyst drivers or an integrated Intel card?

ATIs driver cannot handle video playback/screensaver yet with Compiz running. It's a very requested feature though, so I guess they'll fix that soon. 

If you are very lucky, Catalyst 8.4 will make it into Hardy Heron/Ubuntu 8.04 in April, with video playback support with Compiz on. If not, Envy can always update the latest driver for you..

Sorry if I was a bit unclear on that. Qurrently:

Laptop: Integrated Intel GPU, no problems.

Desktop: ATI x1950xtx, minor problems. I did get the videoplayback to work smooth using VLC, and setting the video output module to X11, so no hard feelings there. I guess the screensaver issue is no big deal, but it is a bit annoying ;) 

Regadring the next driver, will it not be available to Ubuntu 7.10? And this is sceduled for April?

Cheers,
Stefan

---

### Post by Ub1476 on 2008-03-16
Ubuntu 8.04, Hardy Heron, will come with the new drivers from ATI. I'm not sure which version, but surely a 8.*.

The new drivers from ATI has dual-monitor support, hibernate support, Compiz using AIGXL support, and different performance gains etc.. 

Thanks for the tip about VLC though:)

---

### Post by sufslnd on 2008-03-16
> **Ub1476 said:**
> 
Thanks for the tip about VLC though:)

Any time ;) Note that you have to enable advance options, if you cant find the setting :)

---

