---
title: "Xine DVD Audio Device busy"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Gideon on 2005-11-26
Okay, I've searched, and nobody's come up with a satisfactory answer to this yet.

Just upgraded to breezy. Everything worked fine, or so I thought. Then tried a dvd. 

Now, totem using gstreamer falls over with the pad error that's still not fixed. Under totem-xine (and with Xine itself) my dvd starts up, plays any intro, then you start the movie using the dvd menu, and it falls over with an "audio device busy" error.

This persists, even when looking at the running processes indicates that the only thing running that should even be trying to access the soundcard is the xine engine. AVI files appear to play fine.

---

### Post by superm1 on 2006-01-15
Did you ever have any luck resolving this?

---

### Post by Alyus on 2006-01-25
This was happening to me as well. Happens only when I (using alsa) had 5.1 speakers set up in xine/setup/audio.  If this is your setup as well try using 2.1 instead...

---

### Post by superm1 on 2006-01-25
There is a workaround for that problem now:
[http://ubuntuforums.org/showpost.php?p=455464&postcount=6](http://ubuntuforums.org/showpost.php?p=455464&postcount=6)

---

