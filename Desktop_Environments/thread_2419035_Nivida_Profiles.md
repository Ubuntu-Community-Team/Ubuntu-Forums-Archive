---
title: "Nivida Profiles"
date: 2019-05-15
forum: Desktop Environments
---

### Post by toph84 on 2019-05-15
I have a triple screen set up, but one of the screens is actually a TV that I only use when watching netflix etc. in bed. Every time I want to enable it I have to go into the Nvidia software and enable the tv. Inveriably I turn the TV off and the next time I come to use my computer, even though the TV is still turned off, the third screen is still enabled and I have to go back into the settings to disable it again. 

Is there a simple way I can save two profiles to switch between to make transitioning easier? Or to force nvidia to auto-detect which monitors are powered on and enable/disable them accordingly? \

Not sure where this post should live, so apologies if it is not in the correct section, or if it is a duplication.

---

### Post by TheFu on 2019-05-17
I've never gotten nvideo profiles to work. Probably just my personal problem. Sometimes I'm an idiot.

You could script something using **xrandr** to check for changes in the recognized video outputs in log files and enable/disable specific monitors as desired.  It has been a few years since I looked into this.  [https://unix.stackexchange.com/questions/4489/a-tool-for-automatically-applying-randr-configuration-when-external-display-is-p](https://unix.stackexchange.com/questions/4489/a-tool-for-automatically-applying-randr-configuration-when-external-display-is-p) has an example script that might get you started.

The manpage for xrandr has lots of details.

For a quick change, I've found **lxrandr**'s very simple GUI useful.  I use it giving presentations to enable/disable projectors a few times a week.

---

