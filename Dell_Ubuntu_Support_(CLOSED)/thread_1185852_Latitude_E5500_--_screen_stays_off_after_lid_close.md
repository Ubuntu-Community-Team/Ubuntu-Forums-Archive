---
title: "Latitude E5500 -- screen stays off after lid close"
date: 2009-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lykwydchykyn on 2009-06-12
I have a Latitude E5500 which I've had for a few weeks now.  I normally run it plugged in in "performance" mode (so it's not suspending or hibernating).  If I close the lid in performance mode, the screen shuts off (as it should), but when I open the lid it does not come back on.  I have tried any number of things to get the screen to come back on, but nothing works -- the only keyboard commands that seem to do anything are alt+sysrq commands, so I have to alt+sysrq-REISUB any time the lid gets closed.

I noticed that if I'm streaming audio, the audio continues to play indefinitely (hours, even) while the laptop is in this state, so it's not completely locking up.

I also notice that when the laptop comes back up, X11 detects the wrong monitor resolution, and I have to restart the X server up to two or three times before it discovers the correct resolution.  But that only happens after rebooting with alt+sysrq+REISUB, not on normal boot.

Anyone know a workaround for this?  I sometimes like to have my laptop closed but playing music, so I don't want to just set it to suspend.  I've tried different monitor powersave settings, but it doesn't seem to change anything.

---

### Post by punkybouy on 2009-06-13
Any idea what video chipset is on the laptop?  I have seen issues like this on Dells with Nvidia chipsets using the proprietary Nvidia drivers.

---

### Post by lykwydchykyn on 2009-06-13
It's intel:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

I wasn't sure if it was related to the video driver or ACPI.  I am running an updated Intel driver since the one in Jaunty is a bit dodgy.  Maybe I should try rolling back to default.

---

