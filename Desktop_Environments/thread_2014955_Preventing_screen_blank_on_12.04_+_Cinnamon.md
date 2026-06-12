---
title: "Preventing screen blank on 12.04 + Cinnamon"
date: 2012-07-02
forum: Desktop Environments
---

### Post by freemanlowell on 2012-07-02
Hi,

Can anyone tell me how to totally disable all monitor blanking and power-saving in Ubuntu 12.04?

I'm using a fresh install of Ubuntu 12.04 with Cinnamon 1.4 as the basis for locked-down OPAC web terminals in a public library.

The combination of 12.04 and Cinnamon is *spot on* apart from one problem.

The screen blanks after a while, even though I've set the "turn screen off" option in gnome-control-center (System Settings) to "never". I've also tried setting gconf settings as per this post:

[Disable Screensaver (Black Screen) in Ubuntu 12.04 (Precise Pangolin)]("http://www.liberiangeek.net/2012/04/disable-screensaver-black-screen-in-ubuntu-12-04-precise-pangolin/")

I've also trawled through dconf and gconf for Cinnamon-specific entries that might change power settings, but so far haven't found anything.

I can verify that the settings persist after a reboot, that's fine. But the screens continue to go blank when not used. As these are always-on web kiosks, I'm really hoping to find a fix.

Any ideas? Thanks in advance!

---

### Post by gordintoronto on 2012-07-02
Use System Settings, Brightness and Lock.

Perhaps, as well, System Settings, Power-- Don't suspend.

---

### Post by freemanlowell on 2012-07-03
> **gordintoronto said:**
> Use System Settings, Brightness and Lock.

Perhaps, as well, System Settings, Power-- Don't suspend.

I've tried both of those, as well as the gsettings changes I mentioned above. All the power settings look right, and the settings persist after a reboot, but the screen still goes blank on idle. It's really weird.

---

### Post by kansasnoob on 2012-07-03
I have not tried it with Cinnamon, in fact I haven't tried Cinnamon at all, but you might want to try Caffeine:

[https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa)

I use it both in Unity and classic, and there's a brief description in step #12 of my classic (no effects) guide here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

