---
title: "Xinerama, two mouse pointers"
date: 2009-04-20
forum: General Help
---

### Post by TheGolfball on 2009-04-20
I've got Xinerama activated with my desktop spread accross two monitors.  Everyting is working fine but when I move my mouse pointer from one monitor to the next it leaves a "residual" mouse pointer on the other monitor so I end up with a mouse pointer on each monitor (one "active" and the other not until I move back to the other monitor).  Ideally, I want just one mouse pointer that moves accross the whole desktop when Xinerama is on.

A separate question:
Also, when I have Xinerama turned off and I have my two monitors set as two separate displays, all the running programs/windows show up on the left display even if I started them from the right display.  When I am running as 2 separate displays is there a way to get programs/windows running on the monitor that I want instead of always the left monitor.

I'm running two nVidia GeForce 7600 GT cards with one flat panel display connected to each card.  Thanks.

---

### Post by TheGolfball on 2009-04-21
I've searched on this topic and apparently multiple mouse pointer cursors is not a new issue and it has irritated people previously.  It's too bad that it hasn't been fixed because Ubuntu Desktop is very useable.  The multiple mouse pointer issue, however, looks tacky and unfinished.  I don't know if this is a Xinerama problem or the nVidia proprietary video drivers or a configuration problem.  I'l try the nVidia site to see what they have to say.

---

### Post by gwyddon on 2009-04-24
I've found the same problem, but only after upgrading to Jaunty yesterday. My 6 monitor setup was flawless with Xinerama under 8.10. 

I noticed that the upgrade commented out the mouse and keyboard sections of my xorg in favor of HAL.

---

### Post by gwyddon on 2009-04-24
This appears to be the related bug in Launchpad. 

[https://bugs.launchpad.net/ubuntu/+bug/358889](https://bugs.launchpad.net/ubuntu/+bug/358889)

---

### Post by yacine on 2009-04-25
I am having the same problem as gwyddon but with 3 monitors! Any solution?

---

