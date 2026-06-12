---
title: "No sound for videos/flash/etc."
date: 2006-06-16
forum: Desktop Environments
---

### Post by linuxNewb on 2006-06-16
I can listen to mp3s with Rythm box, and I hear system sounds, but I get no audio for any video types in totem, or mozilla-flash-plugin, which is it's own player. Why would these seperate codecs and programs not give sound?

---

### Post by vigleik on 2006-06-16
I don't know about totem, but flash doesn't play nice with other services using the sound server. (It's an oss-alsa thing I think.) Try to turn off any other program that might use the sound server, and _restart_ firefox (I assume you're using firefox). Then try again. That works for me at least. I'm not really sure why restarting firefox is necessary, it's just my experience.

Vigleik

---

