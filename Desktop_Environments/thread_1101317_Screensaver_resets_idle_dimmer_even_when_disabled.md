---
title: "Screensaver resets idle dimmer even when disabled"
date: 2009-03-20
forum: Desktop Environments
---

### Post by mike.freislich on 2009-03-20
Hi,

I like the fact that there is a "dim on idle" setting in the gnome power manager. After much fiddling, I found out how to change the brightness of the dimmer as well as the length of idle time before the display dims. :-) Yay! 
(have a look at the settings in System Tools->Configuration Editor:/apps/gnome-power-manager/backlight)

The next problem I have, is that the Screen-saver is linked to power-management timers (don't understand why these are related) e.g. you can't set the "put display to sleep" or "put computer to sleep" timers to anything lower than (screensaver-timer + 1). I like a really short display suspend timer when running on battery. No problem. I figured that I don't need the screen-saver... so I set it's timer to 1 minute (the minimum) and unchecked the "Active screensaver when idle" checkbox. Then I could set the "display sleep timer" to 2 minutes. Great. A little irritating problem is occuring now that I have done this: After 30 seconds idle, the screen dims... correct... After another 30 seconds (1 minute idle now) the screen switches back to normal brightness. This is due to the screen-saver having reached it's idle timeout; even though it's disabled. The screen doesn't dim again after that. So now, when plugged into ac... the screen dims for 30 seconds on idle, and then goes bright again after 30 seconds. *doh*  What's the point of having the dimmer (and a checkbox to disable the screensaver) if it's just going to go bright again in 30 seconds time?

I want the following behaviour when idle:

ac-power:
- Display dims after 30 seconds
- Display remains dim for 14m30s and then enters sleep state
- No screensaver

battery:
- Display dims after 30 seconds
- Display remains dim for 1m30s and then enters sleep state
- No screensaver

Is this a bug?

I'm running Ubuntu 8.10 on a Dell XPS M1330 laptop

-Mike

---

### Post by mike.freislich on 2009-03-28
bump.

---

### Post by skubisnack on 2009-04-21
Check to see if you have ambient light sensors. I was having the same problem until I disabled that.  It's kind of a cool feature, changing the brightness of your display based on the brightness of your surroundings.  However, it was performing inconsistently and turned out to be more annoying than helpful.

BTW...you can find the ambient controls right above backlight in the configuration editor.

---

### Post by mike.freislich on 2009-04-23
Hi Skubisnack,

Thanks for the response. As far as I know, my laptop doesn't have the physical ambient sensor. Even so, I have tried disabling the ambient light sensor settings in gnome config. Unfortunately this has made no difference. This is definitely related to the screensaver. e.g.

Screen dims after idle for 30 seconds as expected. Then, if I've set my screensaver idle timeout to 1 minute (and unchecked the box to start the screensaver when idle) the display returns to normal brightness in another 30 seconds. I take it, the screensaver resets the dimmer-timer, so that it can be viewed in all of it's technicolor glory. Just seems silly to me that even when the screensaver is disabled, this is still the behaviour, and secondly, that the power management features are directly linked to the screensaver timeout.

Anyway. I've given up on this issue. I guess that whoever coded these features doesn't want to use it in the same configuration as me. This is a bug.

perhaps it is time to download source-code. :(

urg...

---

