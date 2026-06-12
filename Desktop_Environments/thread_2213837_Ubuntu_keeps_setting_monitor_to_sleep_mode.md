---
title: "Ubuntu keeps setting monitor to sleep mode"
date: 2014-03-28
forum: Desktop Environments
---

### Post by frog3764 on 2014-03-28
Greetings to the Group - My system is a dual boot with W7 and U 12.4.  When in Windows my monitor is set to NEVER SLEEP OR TURN OFF which works like it is set for, but in U 12.4 the monitor keeps going to sleep after several minutes.  I've set the power settings U 12.4 to NEVER TURN OFF, but the OS keeps shutting down the monitor.  This is a very pain in the ass as when watching any video I have to constantly move the mouse to keep it from going to sleep.  I want the monitor to STAY ON so I can run my own screensaver slide show too.  I changed monitors from my other pc which runs XP and it too is set to NEVER TURN OFF, but when I swapped to my W7/U12.4 the same problem is still there.  So it's not the monitors, but something in U 12.4 that does this.  The last time I posed this for some help, it never was posted to the forum, so I hope this one will make it this time.  Some help is appreciated to get this problem resolved.

Thanks,
Jim

---

### Post by GigabyteProduction on 2014-03-28
i use xubuntu, so i have xscreensaver installed, there's a blank screensaver in xscrensaver, so you have to do both screensaver setting and power setting, and if you have a laptop, set the settings for all modes (battery, and ac)

---

### Post by frog3764 on 2014-03-28
Hey Gig - Thanks for your reply.  I previously had Xscreensaver installed and used it for my own screensaver slide show, but I kept getting a window that it said it wasn't running, so I always had to "run" it to get it started.  But that didn't effect my monitor as it still would go to sleep after a few minutes.  If I remember right, the screensaver never did come on anyway.  But I need to solve the monitor problem first, then I will work on getting the screensaver to work.

Jim

---

### Post by GigabyteProduction on 2014-03-28
Have you checked all of the power settings?

---

### Post by frog3764 on 2014-03-28
I did check the power settings for the power to stay on, but if there are other settings, then I don't know what they are.

---

### Post by GigabyteProduction on 2014-03-28
if the power settings are set correctly and the screensaver is off completely, then maybe it's a bug, try ```
sudo apt-get update ; sudo apt-get upgrade
``` and see if the updates fixes it

---

### Post by frog3764 on 2014-03-28
Well, there were some itmes that couldn't be fetched.  At the bottom of the screen it says 0 files found etc. 0 files updated etc. etc.  So it looks like nothing was updated.  I think there was a couple of other errors during the process that came up as errors and couldn't find any new ones so the old ones were used.

---

### Post by GigabyteProduction on 2014-03-28
are you using an older version of ubuntu?

---

### Post by frog3764 on 2014-03-28
I'm using U 12.4 LTS

---

### Post by GigabyteProduction on 2014-03-28
i know this part might be a hassle because of all the tabs in the power settings but i don't have the same power settings app as you so it's about all we can do. Could you please send me screenshots of all of the power settings tab? the screenshot app can also do partial screenshots so you won't have to hide everything before you do it, but you have to launch it from the dash instead of the printscreen button.

---

### Post by frog3764 on 2014-03-29
This is the only power settings I know of.

---

### Post by GigabyteProduction on 2014-03-29
Oh i thought the power settings were more extensive in ubuntu aswell... hmm... maybe it actually is in the brightness settings link at the bottom.

---

### Post by frog3764 on 2014-03-29
OK Here is another screenie.

---

### Post by GigabyteProduction on 2014-03-29
Uhg... i really don't know what's causing this, there has to be something we're completely skipping...

---

### Post by frog3764 on 2014-03-29
I'm a relatively newbie here, but I've been messing (trying to learn) with this since last year now and I can't find anyother place to look for any settings or any other folders to look at.  So maybe I'll get some more help here because I'm sure this isn't that much of a problem to solve.  It's pretty simple in Windows.

---

### Post by GigabyteProduction on 2014-03-29
Well ubuntu is designed to be really easy like mac, it's the reason why i don't use pure ubuntu and use xubuntu. Do you think it could be your tv. thinkng it's being smart by shutton off when it sees the image hasn't changed? maybe you can try it on a monitor, or maybe you can leave something on tv. paused (if you can pause stuff) and see if it turns off

---

### Post by frog3764 on 2014-03-29
This is for a desktop pc, and as I stated above, I've already swapped monitors to make sure it's not the monitor, which it isn't.  The problem doesn't exist when I boot to W7 either, so it's someting in Ubuntu that causes this.

---

### Post by frog3764 on 2014-03-31
Does anyone have any more ideas on my problem as it's still an issue here?  I need some HELP to find a solution.

---

