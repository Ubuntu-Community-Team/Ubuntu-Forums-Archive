---
title: "Screen unlock very slow after manager update"
date: 2009-10-23
forum: Desktop Environments
---

### Post by MgFrobozz on 2009-10-23
Sometime in the past week, after update manager ran, my ub9 system (details below) started being very slow to unlock the screen. I timed it today at 71 seconds. During that time, the mouse still moved correctly. The dialog displayed "Working...". When it finally unlocked, everything was fine (the system was normally responsive). "sudo top" reports the highest cpu use in my browser (Opera) at 9%, and the next highest use (Xorg) at about 4%, so I doubt it's attributable to a busy high-priority task.

Any ideas about which update may be contributing?

> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04"

# window manager: gnome

---

### Post by MgFrobozz on 2009-10-25
An additional datum: the same machine is running an ssh daemon. The daemon is now very slow to log in client ssh sessions, around 25 seconds by my measure. Was there a recent change in the authentication libraries that would cause both the screen unlock and ssh authentication to slow down?

---

### Post by MgFrobozz on 2009-11-06
Solved it by removing the avahi-daemon ...

```
apt-get remove avahi-daemon
```
    
Everything was fast-as-lightning immediately afterward. I should have twigged into this earlier, since I have another machine that didn't suffer from the upgrade, and I'd removed the avahi-daemon from that machine just to reduce the number of unnecessary services.

:D

---

### Post by MgFrobozz on 2009-11-11
A caveat: pulseaudio apparently requires the presence of zeroconf/avahi (see [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)). Apparently I need to either figure out how to get pulse out of the way (so that alsa can directly access the sound card), or compile pulse without avahi hooks, or give up audio.

Restoring avahi and dealing with extremely slow sudo is not an option.

---

### Post by durand on 2009-11-11
Pulseaudio should not require avahi unless you need to use networked sound. Have you tried using pulseaudio after removing avahhi?

---

### Post by MgFrobozz on 2009-11-23
The actual problem was with lack of backward compatibility between ubuntu 9.10 and the 2.6.28-15 kernel. Once I upgraded the kernel to 2.6.31-14 the audio came back, I'm not running the avahi daemon, and authentication is still fast (seems like unlock may be a little faster than with 9.04 without avahi).

---

