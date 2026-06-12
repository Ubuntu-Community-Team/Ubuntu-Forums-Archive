---
title: "2 sounds playing at same time, cant"
date: 2005-10-31
forum: Desktop Environments
---

### Post by duffydack on 2005-10-31
Dont know if this is limited to kubuntu or ubuntu in general but while playing my mp3`s in xmms (i prefer it over amarok so would like to still use it) if i receive mail i have a sound notification, however it doesnt play, until the song finishes or i stop it, then the sound plays.....regardless of how long the delay between sound playing and song finishing....any ideas how i can fix it.

Im using alsa in xmms and have tried oss also, and set to alsa in control centre/kde, still same...and ive also set full duplex on to see if it helps any, it dont...
Something else that annoys me also is after mesisn with settings i get "cant open audio" when tryin to play an mp3, have to wait a minute before it`ll play...

---

### Post by Xian on 2005-10-31
Try going into the sound control in the KDE control center and adjusting the time that ARTS waits for the sound daemon to release control to 1 or 2 seconds. This might help some.

---

### Post by duffydack on 2005-11-04
Nope.  Still cant have system sounds playing same time as an mp3.
the song has to finish, either naturally or me stopping it, then the sound plays (even if it was meant to play 10 mins before hand, once song has finished, ding)

anymore ideas?

Edit:  ahhhhhh, installed xmms-arts and used that in xmms as output, is fine now.....

---

