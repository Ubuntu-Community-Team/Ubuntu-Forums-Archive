---
title: "Turning off key repeat."
date: 2009-05-19
forum: Desktop Environments
---

### Post by t.rei on 2009-05-19
Hello.

I can't seem to find an option to turn off keyrepeat in kde4. 

I need to turn it off for some games and apps in wine that go crazy on key repeats.

Any help would be great - a commandline option would be perfect. :)

thanks.

---

### Post by krazyd on 2009-05-19
System Settings > Keyboard and Mouse > uncheck Enable Keyboard Repeat.

```
xset -r off
``` may also work.

---

### Post by t.rei on 2009-05-20
> **krazyd said:**
> System Settings > Keyboard and Mouse > uncheck Enable Keyboard Repeat.

Running Jaunty there is no such option for me. That however is the location I looked first and again and again not trusting my eyes.

> ```
xset -r off
``` may also work.
*edit* it works! Thanks alot. I hope the options to tinker with the rate get added soon. Or is it 'relatively' ok to upgrade to karmic?

Sad thing: this is a rather fresh install with not much tinkered with, that should cause problems like this.

I can turn keyrepeat off by using gnome-keyboard-settings, but this causes the gnome-settings-daemin to run, thus messing up all my font settings. (all fonts way too small, even the kde4 apps, and not reating to change in the settings.)

thanks.

---

### Post by t.rei on 2009-07-22
[http://bugs.freedesktop.org/show_bug.cgi?id=22515](http://bugs.freedesktop.org/show_bug.cgi?id=22515)

It's a X.org bug, known, and hopefully a fix is on it's way. yay.

Now to get wine to accept all my mouse Buttons on my MX Revolution (wheel tilt at last)

> Just confirmed in current git.
I'm not in the position to increase this bugs Priority, but IMO it should be
changed to high. This is now hitting mainstream distributions (eg Ubuntu 9.04)
and quite some apps may be affected, possibly in some subtle ways.
The problem is understood and Daniel seems to have a fix in his repo, so I hope
this will be resolved soon.

---

### Post by t.rei on 2009-09-03
still waiting. :(

---

### Post by satish.bhawra.88 on 2009-09-03
support your key thing by han

---

### Post by ubuntu1sttimer on 2009-09-05
Have a KVM combining two Ubuntu and two Windows machines. When I start the 9.04 machinee it turns on the keyboard's auto repeateeee att a fast rate. The rrepeatts then happen on all the machines.

I can see the tech news headliine now. 

"LINUX BUG TRASHES WINDOWS COMPUTERS".


(Repeats left in on purpose)

---

