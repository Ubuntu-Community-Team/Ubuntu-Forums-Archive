---
title: "Shut off all powersaving, screen still goes black"
date: 2010-06-30
forum: Desktop Environments
---

### Post by Recluse on 2010-06-30
Hello, I'm running Ubuntu 10.04 for a digital signage PC. I ran it on an Ubuntu 9 machine, worked great and got a new machine to put it on so I did so with 10.04 and so far working great, except after an arbitrary amount of time (seems random, I've seen it go half a day with no problem, then do it twice within 20 minutes) the screen acts as though it's going to sleep. The monitor shows No Input and moving the mouse or hitting a key on the keyboard brings it back. I've disabled everything in the power settings, shut off the screensaver, went into the BIOS and changed power savings from S3 to S1 and even tried killing acpid but no luck. I've ran all updates but this persists. Anyone have any ideas?

Thanks!

---

### Post by Recluse on 2010-06-30
Also, I have checked all log files and nothing in there is matching the times the screens go blank. Some of them, like pm-powersave.log don't have timestamps so I can't check for sure unless someone knows how to enable that for this log?

Thanks in adavnce!

---

### Post by cjett on 2010-06-30
My setup does the same and I can't find a reason why either, unless it's the monitor itself going into power save, but I don't know for sure if that is it or not.

---

### Post by rcdavis on 2010-06-30
Same problem.  Screen goes black.  version 10.04,  Screen saver and power saving is turned off.

The only way I can bring back the display is by rebooting.

The problem does not seem to be based on :    Time (seems to be random),  Programs Running (experienced when online and running local programs)  or    Activity level on keyboard or mouse

Unable to locate log file showing any reason for the "black out"

Problem also prompted by screensavers :  antspotlight and GLSlideShow

Seems to be running in Low Graphics mode.  

Monitor shown as Goldstar 22"   Monitor Actually LG Flatron W 2243S. Does not seem to be recognised.

---

### Post by Recluse on 2010-07-07
Sorry for the late reply, didn't see the responses! :)

The monitor will go into standby if it sits without an input for too long, but I've seen it immediately after it blanks and it's not the monitor. Just says no input but if I move the mouse it comes right back up. I had the same monitor running on a different box running Ubuntu 9.04 and the same program I'm running now. I tried killing the gnome-screensaver process and that seemed to help but it keeps reloading so I finally just apt-get remove --purged it. I'll see if that changes anything and reply back.

---

### Post by Linye on 2010-07-07
Maybe try to use Caffeine?

[http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html]("http://www.omgubuntu.co.uk/2009/08/caffeine-delay-screensaversuspend.html")

---

### Post by bigsmitty64 on 2010-07-07
Been dealing with this also and have come to the conclusion that it's just not that big a deal (to me), but I suppose some would have reasons for not wanting this to happen.
As long as you set it to not ask for a password every time then it's a matter of nudging the mouse :)  Plus I don't see the logic behind installing software, (caffeine) that you have to manually click to set, when you can just "nudge the mouse". :)  
Yes this is an annoyance and I would love a "real" fix, but I have a thread on here (among many others) that seem to never get anywhere, A few fixes were suggested but none worked. So, I live with it. PLUS it saves on the power :)

---

### Post by Recluse on 2010-07-07
I'll give Caffeine a try, thanks!

@bigsmitty64 - This is for a digital signage system, so it's a bit of a hassle to pull out the keyboard and mouse just to nudge it whenever it happens. And until people notice it, we have a black screen which defeats the purpose.

EDIT - Went to install the PPA key, had some problems likely because of the firewall but while I was poking around I found another post that matched my situation from another user, and sure enough when I was configuring it I did stop Power Manager from starting up so I reactivated it and I'll post more on if that helped:
--------------------------------------------------------
Man_Beach
A Carafe of Ubuntu

 
Join Date: Dec 2006
Beans: 90
Ubuntu 10.04 Lucid Lynx
Re: Display going to sleep
I have found that the solution is to make sure that the 'Power Manager' option is turned ON in System > Preferences > Startup Applications. If I disable it, the screen goes into power saving mode after about 10 minutes.

So, you need power manager to run in the background in order to make sure that power saving doesn't work. I think.
--------------------------------------------------------

---

### Post by jerry64 on 2010-12-29
I have the same issue, I have also installed 10.04, 10.10 on several systems, laptops and desktops.  What I did notice is this.  Once the system turns on, if there is no user input, the screen will blank out after 10 min.  Once there is user input, the system is fine for the entire day.  Also if you boot the computer and simply nudge the mouse, it will never blank out.  It's just that initial 10 minute window after system bootup that it blanks.  Outside of this it would be great for digital signage.  But as it stands, just not acceptable or realistic for that matter to have someone onsite to bump the mouse.  I also tried Linux Mint with the exact same results.

---

### Post by stinkeye on 2010-12-29
I use the screen saver to display a clock and the monitor blanking used to annoy me.
From what I've read there is a "hidden" power-control option set at 10 minutes, so that no matter what, your monitor gets powered down at the 10-minute point of idle.

....and the fix
```
xset -dpms
```

but

every time you reboot, DPMS will be turned back on.

so you need to add it to startup applications.

```
Name: **DPMS Kill**
Command: **xset -dpms**
Comment: **Stop your monitor being powered down**
```

---

### Post by spamco on 2011-01-13
hello,
 
Can someone tell me wy this is not saved om mij Linux machine everytime i close down the startup application it is gone ? I've tried it about 5 times and it always go out of my startup screen ?
 
Can someone help me please?

---

### Post by stinkeye on 2011-01-13
> **spamco said:**
> hello,
 
Can someone tell me wy this is not saved om mij Linux machine everytime i close down the startup application it is gone ? I've tried it about 5 times and it always go out of my startup screen ?
 
Can someone help me please?
Don't know, but this is what it looks like when I add it to startup applications.

---

