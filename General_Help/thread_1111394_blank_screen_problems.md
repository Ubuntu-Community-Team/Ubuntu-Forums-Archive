---
title: "blank screen problems"
date: 2009-03-30
forum: General Help
---

### Post by Robo495 on 2009-03-30
So recently for no reason I can discern my laptops usability has plummeted. It has been working fine for months on the hardy heron LTS version, kept up to date.

State:
Laptop on and plugged in.
Action:
Remove power cord.
Result:
Blank screen.

State:
Laptop on, running on battery.
Action:
Plug in power cord.
Result:
Blank screen.

State:
Laptop on.
Action:
Hibernate, later resume.
Result:
Blank screen.

Blank screen is that the screen is black, but using fn + brightness up/down can cause the black to shift color slightly, but cannot make out anything of what would be on the screen.

The only way to make the screen usable is to reboot the machine.

Is there any way to make it start acting like a normal laptop again?

Hardware:
Dell Inspiron E1705
ati mobility radeon 1400

---

### Post by Robo495 on 2009-03-31
bump for fix

---

### Post by DeMus on 2009-03-31
> **Robo495 said:**
> So recently for no reason I can discern my laptops usability has plummeted. It has been working fine for months on the hardy heron LTS version, kept up to date.

State:
Laptop on and plugged in.
Action:
Remove power cord.
Result:
Blank screen.

State:
Laptop on, running on battery.
Action:
Plug in power cord.
Result:
Blank screen.

State:
Laptop on.
Action:
Hibernate, later resume.
Result:
Blank screen.

Blank screen is that the screen is black, but using fn + brightness up/down can cause the black to shift color slightly, but cannot make out anything of what would be on the screen.

The only way to make the screen usable is to reboot the machine.

Is there any way to make it start acting like a normal laptop again?

Hardware:
Dell Inspiron E1705
ati mobility radeon 1400

This is a strange problem you have. Do you have any idea when this started and what you have done before that time? Did you install a program, did you change some settings?
Look in System - Preferences - Powermanagement to see if something strange is set there.
Did you by any chance change something in the Bios?

I know these are not real answers, but maybe by reading it and thinking about it, it all comes back to you.
Good luck.

---

### Post by Robo495 on 2009-03-31
I actually did try to figure it out with no luck.

I've gone through my power management settings by hand, nothing seems weird, but just to be sure I made to reclick everything.

I haven't updated or even gone into the laptop's bios for a few years now.

The only changes would be letting ubuntu dl and install the updates it notifies me about.

I'm not sure when it started because at first I thought it was just a random fluke, waking from hibernate with black screen just meant an unlucky hibernate maybe.

But after several time I started to notice the behavior.

---

### Post by DeMus on 2009-03-31
> **Robo495 said:**
> I actually did try to figure it out with no luck.

I've gone through my power management settings by hand, nothing seems weird, but just to be sure I made to reclick everything.

I haven't updated or even gone into the laptop's bios for a few years now.

The only changes would be letting ubuntu dl and install the updates it notifies me about.

I'm not sure when it started because at first I thought it was just a random fluke, waking from hibernate with black screen just meant an unlucky hibernate maybe.

But after several time I started to notice the behavior.

That's often the way things start to go wrong. You don't realize it, until it is too late.

So, it is not the BIOS, we can skip that.

It's not only starting or stopping using the battery, it's also using hibernation, otherwise I would suggest to look for something battery related in your settings.
Does the laptop continue to work, in other words is it only the monitor which causes the problems? Or is the machine "dead"?

I know I'm asking more questions than giving answers to yours, but to be honest, I have no idea what could be wrong here. So I am just fishing for more info. Maybe somebody else, who is reading this thread, has an idea with the info you give.

I just fired up my old laptop which is also using Hardy 8.04 and I will try to find something typical laptop related in it. This might take a while since the old thing, well, it is old. It should have retired a long time ago.

---

### Post by Robo495 on 2009-03-31
Well its hard to tell if its working, but it's not dead per-say.

When coming out of hibernate the cursor will show up, and if I move it around will change as it should for what windows I had open. But if I adjust my screen brightness the cursor immediately dissappears until it is moved again.

The cursor is completely gone and never becomes visible when the power chord is (dis)connected however, so testing much for functionality then is difficult, but I suspect its still working fine.


I thought maybe it was my ati driver, so I just updated to 9.3, but the behavior remains.

---

### Post by Robo495 on 2009-03-31
It seems it was the ati driver.

Or at least disabling fixed the problems.

Something must have died.

---

### Post by DeMus on 2009-03-31
> **Robo495 said:**
> It seems it was the ati driver.

Or at least disabling fixed the problems.

Something must have died.

What did you do to make it function normally again?

---

### Post by Robo495 on 2009-03-31
Ok more news:

Re-enabled the ati proprietary 9.3 driver.

Laptop still isn't exhibiting the black screen bug from before.

Only problem now is that I seem to be stuck in "low graphics mode" and can't for the life of me get the resolution to be anything other than 800x600. The menu before ubuntu fully starts, and the in ubuntu resolution program, both say they detect a generic plug and play monitor (this is a lap top) and won't give any options for changing resolution.


----------------
further
----------------------
disabled proprietary, did various things to the xserver config to reset it, not sure what I did, things still didn't work

used envyng to install ati driver, all is well now

---

### Post by DeMus on 2009-04-01
> **Robo495 said:**
> Ok more news:

Re-enabled the ati proprietary 9.3 driver.

Laptop still isn't exhibiting the black screen bug from before.

Only problem now is that I seem to be stuck in "low graphics mode" and can't for the life of me get the resolution to be anything other than 800x600. The menu before ubuntu fully starts, and the in ubuntu resolution program, both say they detect a generic plug and play monitor (this is a lap top) and won't give any options for changing resolution.


----------------
further
----------------------
disabled proprietary, did various things to the xserver config to reset it, not sure what I did, things still didn't work

used envyng to install ati driver, all is well now

Sorry for the late reply, but I had to work today. Good to hear things are back as they should be. Yes, installing the right video driver can be a pain in the butt. I have had those experiences with nVidia.
Remember what you did, just in case something strange happens again. Enjoy your Ubuntu.

---

