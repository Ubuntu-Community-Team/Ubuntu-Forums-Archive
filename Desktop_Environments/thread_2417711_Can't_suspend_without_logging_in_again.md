---
title: "Can't suspend without logging in again"
date: 2019-04-26
forum: Desktop Environments
---

### Post by peter-a on 2019-04-26
Ubuntu 19.04  

In the last few days, a suspend problem has emerged.

Previously, I would alt-click on the power button in the top right of the screen, which would turn to a pause button, and my PC would immediately suspend.

Now, when I do the same, my screen locks, and if I log back in, the PC immediately suspends.

If I then suspend again 2 or 3 times, it works correctly.

Any ideas on where to look for the cause of this? It means that I walk away from my PC thinking it is asleep when it's actually awake, then when I log in it goes to sleep.

---

### Post by DuckHook on 2019-04-27
Firstly, can't help you directly in light of how I avoid standard versions for exactly such reasons as this and stick to LTS for stability. But the usual remedies apply:

[LIST]
[*]Have you examined your logs? What do *syslog* and *dmesg* say?
[*]Post back any strangeness found therein. Perhaps one of our resident gurus can help.
[*]Search launchpad for this (or similar) bugs.
[*]Did this occur after an update? If so, which one?
[/LIST]
As mentioned, my ability to help is strictly limited, but perhaps this is enough to get you started with others more capable.

---

### Post by peter-a on 2019-04-28
Thanks. Nothing that looks odd in the logs. Updates? Probably, it's adding new updates every day. I'm sorry I can't be more specific as 19.04 is getting daily updates.

I've searched high and low and can't find a similar problem, which is odd as I'm sure I've seen it before, when the laptop lid switch option was the cause (this is a desktop, no lid).

I have kinda solved the problem. In the BIOS there was a setting to allow the OS to choose the sleep state, or always force S3. Switching to the forced S3 sleep option seems to have fixed the problem.

It's as if Ubuntu is sending the S3 sleep signal at the wrong time, so the sleep instruction, the wake and the lock screen are in the wrong order.

---

### Post by DuckHook on 2019-04-28
Good to know you've found a solution. If you consider the matter solved, please mark it so using the thread tools menu at top of thread.

---

### Post by peter-a on 2019-05-20
Well, it turns out that didn't solve the problem, it's back. This is what happens.

When I alt-click the power menu shutdown option to get the pause, the screen locks. When I unlock the screen, the computer sleeps and then won't Wake on Lan, only on the power button.

When I enter into a command terminal sudo pm-suspend, the same thing happens. Upon waking, there are no error messages.

I've tried suspending a few times in a row, and my PC's behaviour is inconsistent:

#1 Alt-click, Screen went dark then reactivated, after 30 seconds PC entered suspend, would not WOL

#2 Alt-click, Entered suspend immediately, would not WOL

#3 Tried sudo pm-suspend, Entered suspend immediately, WOL worked

#4 Alt-click, Entered suspend immediately, WOL worked

Can anyone point me in the right direction to troubleshoot this? Nothing I've found via Google relates to the same problem.

---

### Post by peter-a on 2019-06-24
What I discovered is that sometimes when I alt-click the power icon to suspend, the screen goes blank, then the lock screen appears. If I log in, the computer suspends immediately, but then is already logged in on wake. However, if I leave the computer alone for about 30 seconds, it then suspends normally.

Wake on LAN is still not working.

---

