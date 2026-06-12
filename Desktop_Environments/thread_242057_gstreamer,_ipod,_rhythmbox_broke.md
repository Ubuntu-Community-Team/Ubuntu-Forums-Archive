---
title: "gstreamer, ipod, rhythmbox broke"
date: 2006-08-23
forum: Desktop Environments
---

### Post by vegardh on 2006-08-23
Hello, anyone with any clues on this.
I have Rhythmbox 0.9.4.1 installed via Automatix, and I think the correct set of plugins (even reinstalled them and stuff):
i   gstreamer0.10-plugins-bad
i   gstreamer0.10-plugins-bad-multiverse
i   gstreamer0.10-plugins-base
i   gstreamer0.10-plugins-good
i   gstreamer0.10-plugins-ugly
i   gstreamer0.10-plugins-ugly-multiverse

But rhythmbox still refuses to play my iPod, saying (in .xsession-errors):
** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2

The files themselves are OK, I can play them in for instance mplayer. So it's some rhythmbox-gstreamer problem...

It has worked before, I unfortunately don't know what has broken it...

I have also tried to downgrade rhythmbox to the latest ubuntu one, ie. not Automatix, same problem.

Strangely, it stopped working about the same time I played some ogg files for the first time, related?

Thanks in advance for any clues.

Relevant sources, in brief:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by vegardh on 2006-08-25
Resolved, by (I think) reinstalling/downgrading also faac and faad lib packages from repos, _not_ Automatix.

---

