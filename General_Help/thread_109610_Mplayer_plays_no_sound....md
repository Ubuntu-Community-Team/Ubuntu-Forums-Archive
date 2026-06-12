---
title: "Mplayer plays no sound..."
date: 2005-12-29
forum: General Help
---

### Post by TDonaghe on 2005-12-29
I used Automatix to get my new ubuntu installation off the ground, and I love everything it's done so far.  My biggest complaint right now is that .mov files embedded on web pages have no sounds when played with mplayer.  I see the movie play with no sound.  MP3s in mplayer play sort of, but it's really choppy and cuts to the end of the track after a few seconds.

Is there some software setting I can turn on/off?

Thanks!

---

### Post by jliedeka on 2005-12-29
Check your /etc/mplayer/mplayer.conf, see if there is a line that says "ao=(something)".  It probably shoud be "ao=alsa"

---

