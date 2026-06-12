---
title: "Gaming and nVidia Twinview"
date: 2008-11-30
forum: Gaming &amp; Leisure
---

### Post by btallas on 2008-11-30
I'm pretty noobish when it comes to gaming in linux.  I went with what seems to be the majority when going with a video card.  I originally had an ATI HD 3870 which worked flawlessly under my original install of ubuntu.  The games I ran weren't the fastest they could be but I attributed that to the fact it was ATI and, from what I've read, their driver is inferior to nVidia (in linux).

A little bit about my system.  I'm running 2 lcd panels, one 24" widescreen 16:10 at 1920x1200, one 19" standard 4:3 at 1280x1024.  The ATI drivers picked up this setup and rolled with it.  The only thing I had to do was go to the driver control panel and tell it which monitor was the primary and which was the extended desktop.  After that, no issues whatsoever with any app.  It has been a different story with nVidia.  Installed the restricted driver.  Setup twinview, couldn't get it to set my main 24" monitor as the primary display.  When it would set as the primary, it would default to the secondary resolution, 1280x1024.  To this day, I couldn't tell you how I finally got it to display correctly but it finally is.

When running games, it's a crapshoot.  Finally got WoW to work in wine on my primary panel but it crashes constantly after about 2 minutes of playing (never had the issue on the ATI).  When trying to run Doom 3 (native linux client), it stretches it over both panels instead of just playing on the primary panel (played fine on the primary panel with the ATI with no tweaking).  Heck, even google earth doesn't work with the nVidia driver!!

I know that was fairly long-winded.  I guess what I'm asking is does anyone else run a nVidia card with twinview and monitor's that are different sizes / resolutions?  If so, can you post a link or give me some kind of tutorial on how to get this working?  I'm just about to the point of sending this nVidia (GTX 260 core 216) back and getting a 4870 1gb.  Thanks.

---

### Post by Eazy© on 2008-12-01
Have you tried to use separate X with Xinerama instead? I find works better with Xinerama than with Twinview. The downside with Xinerama is that Compiz does not work with it.

---

### Post by btallas on 2008-12-01
> **Eazy© said:**
> Have you tried to use separate X with Xinerama instead? I find works better with Xinerama than with Twinview. The downside with Xinerama is that Compiz does not work with it.

I will give that a try.  I played with compiz some and it's cool to look at but I notice that just about any game you play they want it disabled.  I will search for some guides on setting up Xinerama.  Thanks.

---

### Post by epitaph on 2008-12-01
I use an Nvidia Twinview setup (no Xinerama) and play games on it. To avoid having games appear in the middle of the two monitors, you'll need to add metamodes to your configuration. I have metamodes for the resolutions I commonly play at. This disables the secondary monitor and places the game in full screen on the primary. I have a script setup that I launch games from that disables things like the screensaver, compiz and a few other things. After the game quits, they are started back up.

A lot of people like playing on completely separate X servers, also.

So, look into using metamodes: [http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)

I think there's a way to add them in the Nvidia control panel though I've never done it that way.

---

### Post by btallas on 2008-12-03
> **epitaph said:**
> I use an Nvidia Twinview setup (no Xinerama) and play games on it. To avoid having games appear in the middle of the two monitors, you'll need to add metamodes to your configuration. I have metamodes for the resolutions I commonly play at. This disables the secondary monitor and places the game in full screen on the primary. I have a script setup that I launch games from that disables things like the screensaver, compiz and a few other things. After the game quits, they are started back up.

A lot of people like playing on completely separate X servers, also.

So, look into using metamodes: [http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html](http://http.download.nvidia.com/solaris/1.0-8762/README/appendix-g.html)

I think there's a way to add them in the Nvidia control panel though I've never done it that way.

Gave xinerama a try and it worked great for WoW, got my correct resolution and was able to use the other desktop to browse and such.  Fired up doom 3 and all hell broke loose.  It seems that the doom 3 engine doesn't work too well with xinerama.  Went back to twinview and am back to where I started.  I will be looking at the metamodes solution next as I really wouldn't need the second monitor when playing a fps like doom 3 or quake 4.  Thanks for the suggestion.

---

