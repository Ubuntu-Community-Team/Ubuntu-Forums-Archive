---
title: "MPlayer package"
date: 2006-04-07
forum: Desktop Environments
---

### Post by motanulincaltat on 2006-04-07
I've installed kubuntu breezy and downloaded the mplayer package. I've changed the video output to xv from the default x11 in /etc/mplayer/mplayer.conf.

Problem: If I go on and start gmplayer from the kmenu, I cannot resize the video window - I mean, I press full screen and I get a black zone around the original size movie window. The command-line mplayer displays fullscreen with no problems.

Fix: Go to gmplayer's video options and click "enable direct rendering".

My 2 cents: I think this should be part of the default. Somebody please inform whoever is building that package to take this under consideration.

Thanks.

---

### Post by localzuk on 2006-04-07
Take a look on launchpad to see who is the maintainer and also to post bug reports etc... [https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)

---

