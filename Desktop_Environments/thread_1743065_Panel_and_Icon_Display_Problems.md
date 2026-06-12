---
title: "Panel and Icon Display Problems"
date: 2011-04-29
forum: Desktop Environments
---

### Post by swhit on 2011-04-29
I've upgraded from 10.10 to 11.04, and now I'm experiencing some problems with the displaying of panels and icons that I'm hoping someone can help me to fix.

Situation:
Running 11.04 in latest virtualbox (4.06, with guest additions installed) on a macbook pro running snow leopard (10.6.7). I'm in gnome classic (no effects) because I'm not yet used to gnome 3 and compiz doesn't run all that well for me in this virtualization set-up. But the problem, described below, is consistent from gnome 3 to classic (with effects) to classic (without effects).

Problem:
When I first log in after a reboot, everything looks great in the default settings (ambiance theme, I think), but after ~ 15 seconds, the panels and icons revert to an odd looking theme that I don't particularly care for. And trying to change the settings in the "Appearance" preferences is of no help, i.e., I can change the themes, but the panels and icons remain in a stock, old-school gnome-ish theme. 

I've attached screenshots to help describe my situation. Is there an easy fix? Can anyone help? I'm thinking of trying a fresh install of 11.04 rather than staying in the upgrade as a possible fix, but it would be nice if I didn't have to do this.

Thanks in advance!

---

### Post by sperlyjinx on 2011-04-29
I'm having the exact same issue running 11.04 as a VMware Server guest.  I found a youtube video of the isssue here:

[http://www.youtube.com/watch?v=M1HWwHhZeTE](http://www.youtube.com/watch?v=M1HWwHhZeTE)

Any help would be appreciated.

---

### Post by sperlyjinx on 2011-04-29
FYI, I've filed a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/773472](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/773472)

---

### Post by swhit on 2011-04-29
Yes, that's the bug. Thanks for linking to the video.

> **sperlyjinx said:**
> I'm having the exact same issue running 11.04 as a VMware Server guest.  I found a youtube video of the isssue here:

[http://www.youtube.com/watch?v=M1HWwHhZeTE](http://www.youtube.com/watch?v=M1HWwHhZeTE)

Any help would be appreciated.

---

### Post by Sam G on 2011-04-29
I posted my issue under another user's thread that was somewhat similar, but the post was more so thanking him for the temp fix terminal command.

[My post]("http://ubuntuforums.org/showpost.php?p=10739786&postcount=14")

Code to fix the theme for the current session:
```
sudo gnome-settings-daemon
```

---

### Post by swhit on 2011-04-29
Thank you - that fix was good for the panels. The icons, however, do not change to the correct theme.

> **Sam G said:**
> I posted my issue under another user's thread that was somewhat similar, but the post was more so thanking him for the temp fix terminal command.

[My post]("http://ubuntuforums.org/showpost.php?p=10739786&postcount=14")

Code to fix the theme for the current session:
```
sudo gnome-settings-daemon
```

---

### Post by Krytarik on 2011-04-30
It seems to be same issue as this:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by swhit on 2011-05-06
FYI, today's updates to 11.04 killed the fix used from post #7. Anyone with a suggestion for a new fix? Sorry I can't figure this out myself.

> **Krytarik said:**
> It seems to be same issue as this:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

Greetings.

---

### Post by micwallo on 2011-05-20
> **Sam G said:**
> I posted my issue under another user's thread that was somewhat similar, but the post was more so thanking him for the temp fix terminal command.

[My post]("http://ubuntuforums.org/showpost.php?p=10739786&postcount=14")

Code to fix the theme for the current session:
```
sudo gnome-settings-daemon
```

Extremely thx for the solution. I have searched about it for half day.

Also thanks swhit's screenshot. I could not find a properly keyword to describe this problem while search on Google.

Just hope this problem can be fixed as soon as possible

---

### Post by asv on 2011-05-20
> **Sam G said:**
> 
Code to fix the theme for the current session:
```
sudo gnome-settings-daemon
```

Thanks for the fix. The issues with VMware have been highly annoying. You would think Ubuntu would get it straightened out before releasing 11.04.

---

