---
title: "No window decorations nor task bar"
date: 2012-07-02
forum: Desktop Environments
---

### Post by etienoo on 2012-07-02
Hi,

I've got a really annoying problem since tonight on my Xubuntu system.

I don't see any window border (with the min/max and close buttons). Furthermore, there are no windows in the task manager (in the task bar, top left part of screen).
Even worse, alt + tab doesn't work anymore. In other words: once a window has opened, I can't switch to another window at all, since there is no way to minimize. Only exiting (using ctr + q) is possible…
And, even more strange, the settings manager prints nothing in the "window" and "window decoration" (?) applications, where there are usually some settings.

This is really annoying!

Note that I didn't change anything recently, and the system has been working perfectly since I installed it a couple of weeks ago.
I might have been doing updates (I always do the security updates, usually without looking very thoroughly at them…).

Configuration : XUbuntu 12.04 64 bits running on Macbook Pro 6.2.
(well, it might be 32 bits, but checking this would require me to exit Firefox, open a terminal, check this, exit the terminal, and open Firefox again…)

Thanks for any hints!

---

### Post by etienoo on 2012-07-02
OK, so apparently I found a solution thank to a [French forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=757791").

I just entered in a terminal:

```
xfwm4 --replace
```

And it worked.

---

### Post by PcMojo on 2012-07-02
Strange, I've recently encountered a similar problem but I am using Gnome 2. I can see my max and min window controls and the taskbar, But when I start an application nothing appears on the taskbar. If I minimize a window it disappears. Something has happened and has to be effecting more than just us. I'm going to start a new thread.

---

### Post by tulipán on 2012-07-11
when i first read your description of the problem i nearly started crying because i have the same problem but couldn't even imagine describing it! and you did and i used your line and it worked! 
vive la communauté ubuntu francophone!!

---

