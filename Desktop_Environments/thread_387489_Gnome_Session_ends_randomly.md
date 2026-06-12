---
title: "Gnome Session ends randomly"
date: 2007-03-18
forum: Desktop Environments
---

### Post by blockcipher on 2007-03-18
Good Morning,

I have an odd issue with my gnome sessions.  I will be working, surfing, etc and gnome will log me off.  It happens randomly and also not when I'm in a certain application.

Any ideas of what could be happening?  Any logs I can look at to see whats causing it?

Any advice would be appreciated!

---

### Post by blockcipher on 2007-03-19
For some reason gnome is working fine.  The only thing I did do is remove Beryl, and xserver.  Re-install xserver and no issues since.

What would cause this?

Thanks!!!

---

### Post by blockcipher on 2007-03-19
Nope.  It crashed just now.

---

### Post by blockcipher on 2007-03-24
I looked in my syslog and I saw the following:

> 

Mar 24 11:19:52 localhost gnome-power-manager: (mikee) DPMS blanking screen because the lid has been closed on ac power

Mar 24 14:22:41 localhost gnome-power-manager: (mikee) Turning LCD panel back on because laptop lid re-opened



I never did that.  So X crashes.  I found this:

[https://bugs.launchpad.net/ubuntu/edgy/+source/xorg-server/+bug/61746](https://bugs.launchpad.net/ubuntu/edgy/+source/xorg-server/+bug/61746)

There is a patch there.  Even though I don't run nvidia or ATI, I have intel onboard do you think it would be an issue me loading this .deb?

I'm running edgy

Thanks all,

---

### Post by blockcipher on 2007-03-29
Out of desperation I upgraded to Feisty beta, and my issue has gone away. I'm really happy

Thanks,

---

