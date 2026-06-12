---
title: "Garbled output from Realplayer smil stream"
date: 2006-08-31
forum: Desktop Environments
---

### Post by justinflavin on 2006-08-31
when i open this smil link in realplayer 10 on dapper, i connect ok, it buffers ok, but the audio output is garbled/messed up

[http://www.rte.ie/smiltest/2fm_new.smil](http://www.rte.ie/smiltest/2fm_new.smil)

its a radio stream from RTE, the Irish national broadcaster.
what could be the problem here, or is this smil stream just not compatible with realplayer 10 for linux?  (i installed replayer10 via the canoncial commerical repository)

---

### Post by roryspain on 2008-06-13
I had this problem with realplayer when listening to any of the BBC radio channels, and it was solved by an update downloaded by update manager just a few days ago. Unfortunately I am new to Linux and had to re-install the system after messing it up. Now awaiting said download. If anyone knows what triggered the download it might solve this problem. Sorry for my ignorance.

---

### Post by ssam on 2008-06-16
see [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/217301](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/217301)

there are fixed packages in hardy-proposed updates, or you can try the following packages:
[http://launchpadlibrarian.net/15055137/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb](http://launchpadlibrarian.net/15055137/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb)
or 64 bit
[http://launchpadlibrarian.net/15055175/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_amd64.deb](http://launchpadlibrarian.net/15055175/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_amd64.deb)

please report on the bug report if they work, or if the dont work.

---

