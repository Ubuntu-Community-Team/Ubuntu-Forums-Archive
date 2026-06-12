---
title: "Update manger/notifier not running"
date: 2005-10-29
forum: Desktop Environments
---

### Post by hashimoto on 2005-10-29
Ladies, Gents,

It seems that my update manger/notifier does not run. There are updates available, but notifier does not pop up. Notification are is on the panel, I have reinstalled update-notifier, but it does not seem to help. Any advice is appreciated. 

Hashimoto

---

### Post by towsonu2003 on 2005-10-29
[QUOTE=hashimoto]Ladies, Gents,

It seems that my update manger/notifier does not run. There are updates available, but notifier does not pop up. Notification are is on the panel, I have reinstalled update-notifier, but it does not seem to help. Any advice is appreciated. 

Hashimoto[/QUOTE]

By "notification are on the panel", by that I assume you mean that weird round thing with arrows on it... And by panel I assume you mean the stuff on the right upper corner of gnome thingy. :)

My notification thing isn't in my panel right now, so I will guess what to do. Right click on its icon on the panel, click on settings, make sure you check the option that says show notifications then close. If there are no updates (control using synaptic), then it won't show itself...

---

### Post by hashimoto on 2005-10-29
[QUOTE=towsonu2003]By "notification are on the panel", by that I assume you mean that weird round thing with arrows on it... And by panel I assume you mean the stuff on the right upper corner of gnome thingy. :)

My notification thing isn't in my panel right now, so I will guess what to do. Right click on its icon on the panel, click on settings, make sure you check the option that says show notifications then close. If there are no updates (control using synaptic), then it won't show itself...[/QUOTE]

Sorry, it's a spelling error: The notification area/applet is in the panel and the update notifier (the round red with arrows) should pop up there, but it doesn't. Yes, there are updates waiting (e.g. sudo) at the moment, I run reload this morning in Synaptic.

Hashimoto

---

### Post by towsonu2003 on 2005-10-29
hoping not to piss you off: did you try completely removing (as opposed to just removing) notifier tru synaptic, including the config files (not sure which ones...)

i'm aware i'm real newbie, but i'm just trying to eliminate what I might do (except reinstalling :) )

PS. this is the config folder: 
.update-notifier

[edit] oh and, can you see update-notif. in the system monitor with seeing all processes enabled?

---

### Post by hashimoto on 2005-10-31
Sorry, was busy all weekend, couldnt' concentrate on this.

> **towsonu2003]hoping not to piss you off?[/QUOTE]
Don't worry, takes more than that  said:**
> did you try completely removing ... notifier ... including the config files
Yes, done that...

[QUOTE=towsonu2003]PS. this is the config folder: 
.update-notifier[/QUOTE]
Yes, and it is empty even after reinstalling notifier

[QUOTE=towsonu2003][edit] oh and, can you see update-notif. in the system monitor with seeing all processes enabled?[/QUOTE]
Yes, it's there.

---

### Post by towsonu2003 on 2005-10-31
[QUOTE=hashimoto]
Yes, and it is empty even after reinstalling notifier
[/QUOTE]

mine is empty too, so that should be fine... have no idea what the problem is though... :(

---

### Post by poptones on 2005-10-31
I just reinstalled hoary yesterday and my notifier isn't running either. I told synapti to refresh the package list and it still doesn't tell me anything. I just told it to "mark all upgrades" and it found all the packages I would expect - all 110 or so.

Yesteray it wouldn't even properly connect to the security server without errors. It does seem something is amiss.

---

### Post by sawjew on 2005-12-06
I have the same problem.  Everything appears to be working but I get no update notification.

Any ideas?

---

### Post by unwoken on 2005-12-11
I too am experiencing this problem.  i have been so busy messing around with my system that i have only just realised that there have been no updates since the first day i installed Breezy.

I recently created a second user for my system, and that user has not been asked to update once, not even on first login (the new user has sudo access).

I read somewhere that installing totem-xine removes not only the default totem, but also some packages(??) which the update notifier needs to run.  does this have anything to do with it?

I would really love to find a solution to this if anyone can help.

---

