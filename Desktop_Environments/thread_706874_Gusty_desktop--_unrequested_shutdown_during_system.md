---
title: "Gusty desktop-- unrequested shutdown during system idle"
date: 2008-02-24
forum: Desktop Environments
---

### Post by batholith on 2008-02-24
My Gutsy system keeps crashing (shuting down) on me..unfortunately it only occurs during system idle...when the system hasn't been used for at least ~45 minutes or so.

The weird thing is that when I go to start the machine back up, it freezes on startup.  I have to perform a hard reboot (hold down the power) to get the machine to do anything.  However on the second reboot, it starts up fine and runs great....until the next system idle crash....

To avoid the crash I used to get around it by playing music on it in the background (via amarok)...However that doesn't seem to be cutting it anymore...it still shuts itself down during "idle" time.

Attached is my system log, broken down in the steps I mentioned above...hopefully someone can point me in the right direction!!

Thanks in advance,
batholith

---

### Post by hugmenot on 2008-02-24
The user's session is only idle if no input has been received for some x minutes. Running Amarok does not keep the session busy (not idle).

Have you tried determining if it really is a fixed time until it happens?

If you set the "time until idle" in the Screensaver Settings to a short value, does it shut down after this exact time? There are also the "Power Management" settings in the same menu. Do they look okay?

Is it an actual shutdown, or does the machine just turn off? A hardware problem, maybe.

---

### Post by hugmenot on 2008-02-24
Okay, your syslog says that g-p-m made your computer suspend bevcause it was idle.

```
Feb 24 15:16:56 ubuntu-desktop gnome-power-manager: (taylor) Suspending computer because System idle
```
and
```
Feb 24 15:17:23 ubuntu-desktop gnome-power-manager: (taylor) Resuming computer
Feb 24 15:17:23 ubuntu-desktop gnome-power-manager: (taylor) suspend failed
```

But it doesn't really look like it did actually do suspend-y things. Very likely (actually it's written in your syslog) the BIOS and/or ACPI for your mainboard are broken. Your PC likely doesn't like this kind of suspend, mine doesn't either. You should disable the supending in the Power Management settings.

---

### Post by batholith on 2008-02-24
No I haven't determined if it's a fixed time or not...but it's *usually* at least 30 minutes...

My screensaver is set for 10 minutes...my "sleep" mode is set to come up after 40 minutes..

Looking at the system log, it's looks like it shut down, or cut-off in this case,  after about three hours of sitting there idle

I guess the machine just cuts off...I down see anything in the system log that indicates otherwise...

---

### Post by batholith on 2008-02-24
> 
hugmenot
You should disable the supending in the Power Management settings.


I'll give it a shot!  Thanks.  I'll post back once I don't have anything to do on the machine :-)

---

### Post by batholith on 2008-02-25
Disabling sleep mode in Power Management appears to have fixed the problem!

Thanks!

---

