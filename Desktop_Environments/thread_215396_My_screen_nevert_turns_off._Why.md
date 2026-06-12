---
title: "My screen nevert turns off. Why?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by lduperval on 2006-07-13
Hi,

Before I upgraded to Dapper, my screen use to turn off automatically after a few minutes. It no longer does so.

I have set power management to put the display to sleep after 30 minutes of inactivity.

I've set the GNOME screen saver preferences to turn on after 10 minutes.

I'm not sure what else to do. ](*,) 

Can anyone help?

Thanks,

L

---

### Post by kahping on 2006-07-21
I have the exact opposite problem to this: i want my monitor to stay on permanently, so i set power management to never turn off my monitor, but it still annoyingly turns off my monitor after approximately 20 minutes idle time.

That's very annoying when i'm watching a video ](*,) 

Checking out gconf-editor, i noticed a dim_on_idle option that's enabled. right now i'm disabling it and testing if that's the cause of my problems.

---

### Post by orb9220 on 2006-07-21
Don't ask me why put a post I saw awhile back was to enable screensaver and set for 1 min and gnome-power monitor to 2 mins.

Let the screensaver start then move mouse open screensaver uncheck when idle.

Wait to see if gnome-power turns off screen at 2 mins if it does then open power mangement and slider to never.

and wait if monitor is still going off then open term and type in xset q
which will show if DPMS is enabled and what the values are for standby shutdown and off are.

xset dpms will enable dpms   xset -dpms will disable  and xset dpms 0 0 0 will set all to never.

Hope one of these work for you.

---

### Post by der_joachim on 2006-07-21
You can also tweak your xorg.conf. In your ServerFlags section, add the options BlankTime, StandbyTime, SuspendTime or OffTime (whichever applies the most) with your desired values. More info on the manpage. :)

---

### Post by orb9220 on 2006-07-22
Sorry many of us have tried adding standby offtime etc... with no success

This is discussed in other threads and seems to be quite a pain in the ubuntu beans.

---

### Post by missmoondog on 2006-07-25
same issue here on all 5 of my kubuntu setups. actually, i did get one to work correctly, but didn't do anything different on that one that i can think of. can't find a decent answer anywhere here on this. did find a reference to this being a bug,but..........

hard to believe that 5 of my machines are acting that weird and it's not an issue i can find anything on readily?

never head this issue in hoary or breezy or ubuntu with gnome.

---

### Post by kinematic on 2006-07-25
i also had a problem with dpms and after the command "xset dpms 600" the standby time was set to 10 mins and it has worked since then.

---

### Post by missmoondog on 2006-07-25
does the monitor actually go all the way to sleep or look like it's stuck between sleep and awake? kind of a dull, ugly grey and does the light on the monitor itself flash?

edit:
i just tried with the setting at 60. monitor is in that mode that looks like it's between modes. light on monitor is not blinking either.

---

