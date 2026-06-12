---
title: "[Kubuntu] Unable to logout/shutdown/restart....amarok doesn't play anything...."
date: 2009-11-26
forum: Desktop Environments
---

### Post by sccolbert on 2009-11-26
After yesterday's libvorbis updates, I found myself not able to shutdown/restart/logout via the kde menu, and a `sudo shutdown now` would kill the kde session, but still not fully shutdown. I had to manually kill the machine via the power button.

I also had the symptom that Amarok wouldn't play anything. Running `amarok --debug` and googling the output brought me to this post from ArchLinux:

[http://bbs.archlinux.org/viewtopic.php?id=82930](http://bbs.archlinux.org/viewtopic.php?id=82930)

The solution there fixed my problem. It seems the vorbis updates borked something with xine and the cache needed to be purged. The following command solved my problems. 

rm ~/.xine/catalog.cache

---

