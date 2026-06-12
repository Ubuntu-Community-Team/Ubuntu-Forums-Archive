---
title: "Monitors blank with docked laptop"
date: 2009-12-28
forum: Desktop Environments
---

### Post by mazz0 on 2009-12-28
I use a laptop in a laptop dock at work, with two monitors plugged into it.  The problem is, there's no option in the power manager to not blank the screen when the laptop lid is shut, so to use it in my dock I have to jam the lid open with something, other wise my monitors go blank.

I'm sure (kinda) there was an option in the power manager in 9.04 for "When laptop lids is closed 'Do Nothing'", but there isn't in 9.10.  Ideally you'd have different behaviour depending on whether external monitors are in use.

---

### Post by swapz83 on 2010-01-11
Running into the same problem. However, rebooting the laptop and keeping the lid closed during reboot allows me to use the monitor plugged in without opening the lid. Wierd workaround :)

---

### Post by llawwehttam on 2010-01-11
erm ... I think it in System>preferences>power management

---

### Post by mazz0 on 2010-01-14
The only options for "When laptop lid is closed" are
"Blank Screen"
"Suspend"
"Hibernate"
"Shut Down"

No "Do Nothing" option.

You're right swapz83, if you have the lid closed when you boot up it's fine, it's when you close the lid that it powers all the monitors down, not just the laptop one.  I suppose the bug is that it blanks all screens, not just the laptop one.  It also doesn't seem to notice hot-plugging monitors, and it doesn't recognise different resolutions when it boots up.  For example, when I boot up unplugged from the dock the resolution is far too high for my laptop screen.  I suppose I should raise these as bugs.

---

