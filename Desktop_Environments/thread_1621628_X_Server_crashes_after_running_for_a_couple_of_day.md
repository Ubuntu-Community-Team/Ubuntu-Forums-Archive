---
title: "X Server crashes after running for a couple of days"
date: 2010-11-14
forum: Desktop Environments
---

### Post by armware on 2010-11-14
My laptop is usually on constantly, and I've noticed that a couple of times a week the hard drive activity goes crazy and slowly locks up over a few minutes.

The hard drive activity light goes solid, everything gets choppy (I'm assuming it's waiting on the hd io) even my audio player (amarok) starts skipping, looping, stops, continues. Almost like it's doing a massive log dump. If I allow it to do its thing, it takes upwards of 10 minutes before the X server resets, and I'm back at the KDM login screen.

I did search through /var/log and /tmp for files over 10mb, though I found nothing helpful. How can I figure out where to start looking?

KDE v4.5.1

---

### Post by armware on 2010-11-24
it's happened 4 times since the previous post. this last time it happened i was lucky enough to have htop open in yakuake.

i spotted the process vlc was claiming 81% mem usage and climbing.

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/575460]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/575460")

[http://trac.videolan.org/vlc/ticket/3657]("http://trac.videolan.org/vlc/ticket/3657")

---

