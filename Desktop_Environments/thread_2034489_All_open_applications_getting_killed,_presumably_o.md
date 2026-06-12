---
title: "All open applications getting killed, presumably on sleep/system standby."
date: 2012-07-28
forum: Desktop Environments
---

### Post by clammmm on 2012-07-28
Acer TravelMate C300, 1GB RAM, 80GB HDD.  Xubuntu 12.04, Precise Pangolin.

The title says it all.  I leave a bunch of apps up, go away for awhile, come back a day later, log back in, and there's an empty desktop staring at me.  I'm not sure if the thing is randomly rebooting while I'm away, of if it's just going into standby and killing everything beforehand.  And I'm too much of a bash-n00blet to know where to look to find out (system log?).  The laptop is plugged in the whole time, sitting still, on a desk, not getting bumped around or anything.  It's got a brand-new new battery.  Any help would be appreciated.

---

### Post by Peripheral Visionary on 2012-07-28
Sounds like it's preconfigured to go off after a certain amount of idle time. 

Right-click the desktop, then choose

**Applications > Settings > Settings Manager > Power Manager**

and check the settings there. On battery the default may be to shut off after a certain idle time. I don't have a laptop, but even my desktop is set up by default to "go to sleep" after idle time of more than a few minutes, even with the screensaver disabled.

---

### Post by clammmm on 2012-07-28
> **Peripheral Visionary said:**
> Sounds like it's preconfigured to go off after a certain amount of idle time. 

Right-click the desktop, then choose

**Applications > Settings > Settings Manager > Power Manager**

and check the settings there. On battery the default may be to shut off after a certain idle time. I don't have a laptop, but even my desktop is set up by default to "go to sleep" after idle time of more than a few minutes, even with the screensaver disabled.

Thanks very much for the reply, but nope!  As a matter of fact, this just makes things weirder.  According to every tab in the Power Manager dialogue, all the settings were already defaulted to "never," as in "never suspend, sleep, hibernate, whatever for any period of inactivity."  This makes me even more confused, as obviously SOMETHING is causing this thing to go into a turn-screen-off-and-require-password-to-resume state.

Oh, I forgot to mention that I'm using a scavenged IBM adapter on this thing, and the battery says it wants 14.8v @ 4300 mA, while the adapter has a nominal output of 16v @ 4.5 A (4500 mA).  I've been actively using this thing plugged in for hours with no perceivable issues while using (no random shutoffs or overheating, etc), which is why I didn't think to mention it initially.  Then, when I did think about it, I was afraid it might make people go "oh, that must be the problem" and ignore the thread.  But in the interests of full disclosure, I guess I should mention it.  I'm fairly convinced this isn't the/an issue, though, but if any hardware gurus out there who know what they're talking about think otherwise, then by all means please speak up.

---

### Post by clammmm on 2012-07-28
P.S. Screensaver is set to "black out" after 10 minutes, "Cycle" (whatever that means; maybe that's the problem?) is set to 10 minutes, but "Lock Screen After" is un-check-marked.  Also, I had to finger the mousepad to pull it out of blackout to check--as I had left it for an hour or so since last messing with it--and I was not at that time asked for a password, which to me indicates that there is some erratic stuff going on up in here.

---

### Post by clammmm on 2012-07-28
Is there a way I can look at a system log to see when and what the last major system events were? --such as restarting, killall, etc?

Also, I seem to remember back in my early 2000's debian desktop days that there was a ctrl+function-key combo that would let me look at the live "verbose system console" or whatever you call it; you know, like a realtime, terminal-based, no-input-allowed monitor that would show you the line-by-line scripts running in the background.  But I can't seem to find that key-combo with any *buntu system.

---

### Post by Peripheral Visionary on 2012-07-29
Try completely disabling the screensaver, turning it OFF. If that doesn't help, 

You can click [here]("file:///usr/share/xubuntu-docs/pm-suspending.html") to learn more about suspension and hibernation features of your Xubuntu (only Xubu users can use that link, it's a file rather than a web page). I found this interesting quote on that page:

> Some computers may have problems going into certain power saving modes.  	The best way of checking if your computer can handle a power-saving mode  	is to try to switch to that mode and see if it behaves as you expected.  	Always make sure you save important documents before suspending or  	hibernating. 	

It's possible to *manually* suspend or hibernate too instead of walking away and waiting to see what happens: **Right-click > Applications > Logout >** choose your option.

---

