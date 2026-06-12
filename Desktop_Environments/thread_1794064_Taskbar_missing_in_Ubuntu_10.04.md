---
title: "Taskbar missing in Ubuntu 10.04"
date: 2011-06-30
forum: Desktop Environments
---

### Post by Steve Francis on 2011-06-30
After upgrading to Lucid, there is no any taskbar or main menubar in my Ubuntu 10.04 (Lucid  Lynx) machine.

I can correct this by typing
```
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```However, when I reboot, the taskbar and toolbar were missing again.  How do I get the system to remember the position of the tool and task bars in the next time?

---

### Post by Krytarik on 2011-06-30
Maybe they are just not coming up for some reason right after login? This can be caused by faulty video driver settings, or the driver itself. Did you try just restarting gnome-panel without the resetting part!?

Greetings.

---

### Post by Steve Francis on 2011-07-02
> **Krytarik said:**
> Did you try just restarting gnome-panel without the resetting part!?

I tried without resetting and the menu bar is restored OK.

I think I'm going to do a clean install as there are several problems at boot up (sreadahead not found, two simultaneous 'welcome' wav files).

Thanks for your reply.

---

### Post by Steve Francis on 2011-07-03
Have just done a fresh install of 10.04.2 - and the menu bar at the top and task bar at the bottom are still blank!

Is this a bug?

---

### Post by Steve Francis on 2011-07-03
> **Krytarik said:**
> Maybe they are just not coming up for some reason right after login? This can be caused by faulty video driver settings, or the driver itself.

My video card is a Matrox Millenium G550. 

> **Steve Francis said:**
> Is this a bug?

Since my previous post, I've discovered that there is a bug related to the Matrox card:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/572550)

I used Synaptic Package Manager to "completely remove" compiz and compiz-core, logged out, logged back in, then reinstalled compiz and compiz-core (again with Synaptic) and it seems to be fine now. It didn't work unless I logged out between removing and reinstalling.

I won't mark this as "solved" until I've tested the system for a little while. (Some irritations still exist e.g. the Ubuntu start up sound is distorted)

---

