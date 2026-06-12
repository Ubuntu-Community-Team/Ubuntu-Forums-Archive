---
title: "administrator mode problem"
date: 2006-02-17
forum: Desktop Environments
---

### Post by tiodan on 2006-02-17
i just installed kubuntu last night, and am having problems accessing admin mode to adjust my clock (i think i screwed up during the install). kde displays my time as though i am on UTC (note: it's set to local timezone when i right-click and check under 'show timezone) and when i try to change it via kde's system settings utility, it doesn't recognize my password. i have tried everything in the RootSudo ubuntu wiki: i tried using visudo, adding the line 'dan ALL=(ALL) ALL'; i made sure 'dan' was in the admin group according to KUser. i then restarted kde, to no avail. i then rebooted, just to be really really sure. still nothing? what's going on?

---

### Post by gingermark on 2006-02-17
Just to confirm, your password doesn't let you access Admin mode in the Control Centre, but it works elsewhere? You can run Adept, for example?

---

### Post by tiodan on 2006-02-17
exactly. i can run adept (and have successfully installed several packages), but can't access any of the items in kde's control panel that require administrator mode. 

PS. adept hasn't been running flawlessly (it refuses to install either of the required packages needed for mp3 playback), but that's another question for another thread...

---

### Post by tiodan on 2006-02-17
ok, this keeps getting stranger. i know i sound like an idiot, but i swear what i say is true. the administrator problem seems to have gone away; i can now change the date and time, but when i do the time displayed in the kde panel DOES NOT CHANGE. i go system settings>date&time>i enter my password>i fix the date and time> i hit 'apply'> i exit the system settings. the clock keeps on displaying UTC, and when i go back to the system settings, my changes have disappeared. i know this sounds like i'm being sloppy, but i tried this 4 times, all with precisely the same result. baffling...

---

