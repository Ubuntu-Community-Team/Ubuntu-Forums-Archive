---
title: "What logs do I look at after a crash/freeze?"
date: 2009-04-11
forum: General Help
---

### Post by Volt9000 on 2009-04-11
Ubuntu just crashed on me for the first time.
Well I wouldn't call it a crash-- it was just sitting there, torrenting away, and I come back after an hour or so and get out of the screensaver, only to find my primary monitor is completely blank and my secondary monitor only has the desktop wallpaper (it should have a panel at the bottom along with a few apps I had open.) I tried pressing the usual keys to bring up a terminal screen (Ctrl+Alt+F keys) but it didn't work so I had to do a hard reset.

Now which logs do I look at to figure out what happened? I know they're stored in /var/log but there's a bunch there and I wouldn't know where to begin.

Can someone point me in the right direction?

---

### Post by cariboo on 2009-04-11
I would look in Xorg.log, as it seems to be a video problem.

Jim

---

### Post by Volt9000 on 2009-04-11
Ok, I have no Xorg.log but I have Xorg.0.log and Xorg.failsafe.log.
I checked both but could find nothing of note. What should I be looking for?

The problem is neither of these logs are timestamped so I'm not sure how far back I should be going.

---

### Post by Twitch6000 on 2009-04-11
> **Volt9000 said:**
> Ok, I have no Xorg.log but I have Xorg.0.log and Xorg.failsafe.log.
I checked both but could find nothing of note. What should I be looking for?

The problem is neither of these logs are timestamped so I'm not sure how far back I should be going.

post both of those logs it so we can help you find the problem :).

---

### Post by Volt9000 on 2009-04-11
Alright, here they are.
Thanks in advance!

---

### Post by Twitch6000 on 2009-04-12
I could be wrong,but this seems like one of those quirks or bugs.

I would just restart and see if that fixes your screens.

If it does good.

However if you go into screensaver mode then get out of it and the screen does that again the problem is probably a bug you should report.

---

### Post by Volt9000 on 2009-04-12
Alright, thanks for taking a look.
If it is indeed a one-time fluke, that's fine, but even those are irritating, because I hate not knowing what causes things like that.

As an aside, in case this DOES happen in the future, what should I be looking for in the logs?

[Edit]
I should have mentioned this before, as I just saw it again when I tried restarting now.
When my computer froze the first time and it restarted, after the normal Ubuntu logo with progress bar, the screen goes to all-text and sits there. I can switch between terminal screens no problem, and after about 20 seconds the text screen displays some extra startup stuff and the login screen appears. Problem is it scrolls too fast for me to see and it's gone.
I saw that something failed startup, but I think it had to do with VirtualBox, saying it's not a virtual machine so it's not a big deal.
Which log contains a list of these startup items?

---

### Post by XelderX on 2009-04-12
I've also been having the "locked up" problem when I come back from being in screensaver mode. It's not happening every time, but I've had to do a hard restart every time it occurs. The mouse and keyboard do not function at all and it basically requires me to unplug the power from my tower to force a restart. When it reboots everything is fine. This has probably happened 4-5 times in the last week.


Update:

It just happened again. That's twice in the last hour. I'm going to disable the screensaver and just turn my monitor off for the next few days to see if it still occurs.

---

### Post by Volt9000 on 2009-04-14
*bump*

Anyone know where I can look to find what's causing that delay in startup?

---

### Post by XelderX on 2009-04-14
No idea on the startup delay. I came home from work today and mine was locked up again. I guess it isn't an issue with the screensaver. I rebooted it to an earlier Kernel release to see if it's something in the newest updates.

---

