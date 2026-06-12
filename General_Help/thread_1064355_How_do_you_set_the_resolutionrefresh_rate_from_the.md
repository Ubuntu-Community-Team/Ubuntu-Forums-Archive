---
title: "How do you set the resolution/refresh rate from the command line?"
date: 2009-02-08
forum: General Help
---

### Post by Pikestaff on 2009-02-08
So I've been using Kubuntu 6.06 for... a looong time.  I could never update it because all subsequent versions of 'buntu did not work with my wireless card.  No idea why, they just didn't.

Anyways!  Now I have hardwired internet and that problem is no more!  Hence my decision to nab Kubuntu Hardy and do a fresh install.

Booting up the LiveCD got me the "Input Signal Out of Range, Change Settings to 1280x1024, 60Hz" that I'm rather used to by now.  So I booted it up in Safe Graphics mode, had no problems, and installed.

Trying to boot into my new shiny Kubuntu install got me the same bunch of colorful lines and Out of Range message.  No problem, I thought to myself, I'll just boot into recovery mode and reconfigure xorg, since that's what I would do in Dapper and it always worked like a charm.

Slight problem though.  When I do a dpkg-configure xserver-xorg in Hardy, it doesn't seem to present me with nearly as many options as it did in Dapper.  So I can't seem to change my resolution and refresh rate from there.  So I can't log into my Linux without getting that error message.

So what I'd like to know is: how can I change all of that from the command line, since reconfiguring xorg doesn't seem to want to cooperate the same way it used to?  Much thanks in advance, my friends <3

---

### Post by Bozodog on 2009-02-08
I just downloaded and installed Ubuntu 8.10.  

I mistakenly set the monitor to an unsupported resolution, and when I boot I get the "setting not supported" message on my monitor. 

Like you, I need to know how to set the resolution from the command line.  I have a Dell GX270 that, I believe, uses Intel graphics.

---

### Post by Bozodog on 2009-02-09
So I fixed it by hooking the computer up to another monitor.  It booted fine, I changed the resolution settings, and hooked it back up to the original monitor.  Now the display is just fine.

While that worked, I would like to know the correct way to change the resolution from the command line at boot up.

Thank you.

---

### Post by Pikestaff on 2009-02-09
Hmm, thanks for the info regarding a second monitor, I may have to try that, but it would be nice to get an answer on this, I do agree.  So bump!

---

### Post by photon_man62 on 2009-02-09
No idea about the refresh rate, but here's for the resolution:

```
xrandr -s desiredresolution
```

Where desiredresolution is your desired resolution, of course.

OR

```
xvidtune
```

I believe this automatically sets the resolution optimal for your monitor.

---

### Post by Pikestaff on 2009-02-09
Alright, I went ahead and did this with a second monitor.  What I did was:

1.) Got a second monitor that I could "see" with
2.) went into displayconfig (system settings -> Display)
3.) Went into hardware and selected my monitor as being the correct size and type
4.) Turned off the computer, hooked up "wanted" monitor, and booted

That got me into a 800x600 display but then I went back into displayconfig and got the resolution I want.  Kind of a messy workaround but it worked. :P

Keeping this thread open (instead of solved) in case someone knows the answer to the original question cause I would be curious.  However, if a mod chooses to close the thread I won't question them.  Thanks to those of you who did contribute to this thread so far and happy Linuxing!

---

