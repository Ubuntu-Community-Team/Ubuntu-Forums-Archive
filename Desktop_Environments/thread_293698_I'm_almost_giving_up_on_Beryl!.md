---
title: "I'm almost giving up on Beryl!"
date: 2006-11-05
forum: Desktop Environments
---

### Post by miceagol on 2006-11-05
I have been living a happy life with Beryl for a while, but I have one major issue I want to fix: Playing videos (movies etc.) is veeery choppy, and that is unacceptable. I have searched for answers on the forum, but there seems to be no simple solution to this. :( 

Running glxinfo showed "Direct rendering: No", so I figured it might be the Nvidia drivers, and tried to uninstall the Nvidia drivers following method 1 of [this]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") guide. But that just made x server crash, and left me alone in the bash. There I managed to reinstall the drivers, but still x server would crash upon startup. I could now enter gnome through startx, and I noticed that Beryl was down and playing videos was smooth now (glxinfo now said "Direct rendering: Yes"). But still I had the x server error at start up with no GUI login window. Suddenly I noticed this in the x server error:
```

GDM: xserver not found /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo - kb -auth /var/lib/gdm/:0, xauth -nolisten tcp vt7

```
With this I found out I was missing xsession-xgl, which was probably removed when I removed the Nvidia drivers. Installing this package I got everything back, also the choppy movie playback (btw, screensavers and browser scrolling are also choppy).

Now my questions to you: 
[B]Do any of you know a fairly easy way to get smooth playback of movies with Beryl? 
Do all of you have this problem with Beryl? 
Does it have something to do with direct rendering?[/B]

And finally... Can I shut down Xgl without crashing the x server by doing this?
```

sudo ln -sf /usr/bin/Xorg /etc/X11/X

```
And get Xgl back with this?
```

sudo ln -sf /usr/bin/Xgl /etc/X11/X

```

---

### Post by arsenic23 on 2006-11-05
What's your cpu usage while idling ?

---

### Post by miceagol on 2006-11-05
> **arsenic23 said:**
> What's your cpu usage while idling ?

Idle usage for Xgl is around 2%, while total lies around 5%. But I see now that when I start a movie playback, the cpu usage of Xgl pops up to **100%**, while the movie application is given minimal cpu. Why does this happen? Why should Xgl get so much cpu when it's not doing the work... :confused: 

Here's the relevant specs (older system, but should be ok): AMD Athlon 1.2 GHz, 1 GB memory and nVidia GeForce2 32MB GTS video card.

---

### Post by miceagol on 2006-11-05
:KS 

Just thought I'd post a screenshot (example with tvtime)...
[http://folk.uio.no/michaeka/tilalle/Screenshot.png]("http://folk.uio.no/michaeka/tilalle/Screenshot.png")

---

### Post by zgornel on 2006-11-06
What video driver are you using ? (xv, X11, opengl ?)

---

### Post by miceagol on 2006-11-06
> **zgornel said:**
> What video driver are you using ? (xv, X11, opengl ?)

The video driver has nothing to do with it. As I said, playing movies was smooth when Xgl wasn't active (before I reinstalled xsession-xgl).

Anyway, I think I'm using xv to play movies.

---

### Post by Max_Might on 2006-11-06
If you have Beryl, glxinfo will allways show "Direct rendering: No".
I dont know why but thats normal, its not a bug .. i think.

---

### Post by miceagol on 2006-11-06
> **Max_Might said:**
> If you have Beryl, glxinfo will allways show "Direct rendering: No".
I dont know why but thats normal, its not a bug .. i think.

Okay, so then I know at least that's normal. :) But what about Xgl stealing 100% CPU when it's not doing the work. Anyone have that too?

---

### Post by angkor on 2006-11-06
Since you have an Nvidia card you could try beryl without XGL using the new beta driver instead.

I'm running it atm (direct rendering = yes) but I didn't experience your problem when I was still running xgl.

---

### Post by Eversmann on 2006-11-06
beryl with AIGLX runs awesome, i recommend it far more than xgl.

---

### Post by JayTee on 2006-11-06
I'm running Beryl with XGL using NVidia's 1.0-8776 version driver with my eVGA GeForce 6200 LE. The CPU is a Pentium D 940 and most of the time the movies are playing neither of my cores is even hitting anything close to 50%. I just installed this update on Sunday. I had no problems with playing DVD movies or AVI files. The only choppy vids I get are through Firefox when viewing CNN videos which use mplayer-gstreamer plugin to emulate Windows Media Player. Those tend to be choppy at first and then stablize. Otherwise I've had no problems viewing movies.

---

### Post by tronica on 2006-11-06
> **Max_Might said:**
> If you have Beryl, glxinfo will allways show "Direct rendering: No".
I dont know why but thats normal, its not a bug .. i think.

Not with aiglx, i had this same problem, and decided to use aiglx and the problem was solved, plus theres no fuss with xgl.

---

### Post by iovar on 2006-11-06
> **miceagol said:**
> The video driver has nothing to do with it. As I said, playing movies was smooth when Xgl wasn't active (before I reinstalled xsession-xgl).

Anyway, I think I'm using xv to play movies.


The driver may have everything to do with it. 

AFAIK Xgl (which is demo, as in demonstration and not everyday use)
has issues with the Xv extension, so it overrides it with a dummy one. 

It is like the indirect  implementaion of Mesa,which it's using for 3d. 

That's why it's called a hack anyway...

---

### Post by miceagol on 2006-11-07
> **angkor said:**
> Since you have an Nvidia card you could try beryl without XGL using the new beta driver instead.

Where do I find the beta driver, and should I then skip the Xgl part when installing Beryl?

---

### Post by miceagol on 2006-11-07
> **tronica said:**
> Not with aiglx, i had this same problem, and decided to use aiglx and the problem was solved, plus theres no fuss with xgl.

> **Eversmann said:**
> beryl with AIGLX runs awesome, i recommend it far more than xgl.

Seems like many of you say aiglx is better, so I'll try that out instead. :-D 
Removing Xgl crashed the X server last time, so can somebody confirm if this command disables Xgl and replaces it with Xorg:
```
sudo ln -sf /usr/bin/Xorg /etc/X11/X
```

---

### Post by miceagol on 2006-11-07
> **JayTee said:**
> I'm running Beryl with XGL using NVidia's 1.0-8776 version driver with my eVGA GeForce 6200 LE. The CPU is a Pentium D 940 and most of the time the movies are playing neither of my cores is even hitting anything close to 50%. 

In two months time I'm buying brand new parts for my computer. Will probably get an Intel Core 2 Duo CPU among other things, so that might fix my problems alltogether. :-D

---

### Post by angkor on 2006-11-07
> **miceagol said:**
> Where do I find the beta driver, and should I then skip the Xgl part when installing Beryl?

You can follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=263851") to set it up.

---

