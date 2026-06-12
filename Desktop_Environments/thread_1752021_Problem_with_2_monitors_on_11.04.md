---
title: "Problem with 2 monitors on 11.04"
date: 2011-05-07
forum: Desktop Environments
---

### Post by SeanGordon on 2011-05-07
I have done a clean install of Ubuntu 11.04. My HP ProBook 4520s notebook computer exhibits the following problem.

I use the notebook with lid closed, connected to Samsung SyncMaster P2350 23" LCD Monitor. When Ubuntu boots it selects 1024 x 768 resolution. I then go into the display settings and notice that it is set to display the same image on both monitors. If I uncheck this setting, I see the Samsung and can make changes to the resolution settings of both laptop monitor and Samsung monitor, however, when I click Apply, the Samsung I am viewing goes blank. If I then open the laptop lid, it too is blank. After a cold reboot, I am able to get the Samsung monitor to act as a desktop estension perfectly, but not as the only monitor with the laptop screen turned off. Any attempt to turn off the laptop monitor in the settings results in no screen at all.

In the office, I have an LG 19" Flatron monitor, and Ubuntu does not exhibit the same problem. I can boot up with lid closed, and the Flatron works fine as the only monitor and at it's native resolution all by itself.

Booting with lid open, and then closing the lid, also results in the Samsung going blank, but probably for the reason that there is no option in power management to DO NOTHING when the Lid is closed.

It seems that Ubuntu have forgotten about people who use their laptops as desktops in this way.

I am not happy to run with the laptop open and split screens, as I cannot get the launcher into the Samsung, and everything has to be moved over all the time, is there any work around that anyone may know about?

The HP ProBook uses Intel Graphics, for which there are no particular additional drivers I am told. The problem also happened in Ubuntu 10.10, but before 10.10 I don't recall ever having this problem (from 7.04 thru 10.04)

---

### Post by teachop on 2011-05-07
> **SeanGordon said:**
> There is no option in power management to DO NOTHING when the Lid is closed.
I don't know why they took that away.  The option is actually still there if you start up "gconf-editor" and then go to:
apps | gnome-power-manager | buttons
There you can set lid_ac value to equal "nothing".

That doesn't solve all your problems, but it might get one little bit of it...

---

### Post by SeanGordon on 2011-05-14
Thanks for that. This is probably not the right forum for this, but I can't help fealing that, if Ubuntu is to succeed in their goal to provide a truly acceptible Windows alternative, we need to see Linux moving away from the technical realm into the world of Joe Average User - which would mean that any editing of config files would not be a solution. I think I will wait until Ubuntu addresses the problem in a new build, and then try again. Appreciate you help.

---

