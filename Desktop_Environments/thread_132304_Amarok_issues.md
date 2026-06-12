---
title: "Amarok issues"
date: 2006-02-18
forum: Desktop Environments
---

### Post by da1 on 2006-02-18
Hello all, i've recently moved over to kDE and amarok has become my new music player.
I'm however having issues... each time i wanna play a song this message appears at the bottow of the player:
Gstreamer error: gstmad.c(1206): gst_mad_check_caps_reset:
/thread/decoderbin19/mad20 Failed to (?)e

So pleez somebody help me with this basic error, don't laugh, i never was computer literate, however i've been trying my luck with ubuntu since october and slowly getting better and the terminal is weird, but i can do stuff there which is super cool for a noncomputer lover!!
thanx for the cool forum

---

### Post by aysiu on 2006-02-18
It's not looking good for you... only [three Google results on your error](http://www.google.com/search?hl=en&q=Gstreamer+error%3A+gstmad.c%281206%29%3A+gst_mad_check_caps_reset%3A&btnG=Google+Search).

---

### Post by metwo on 2006-02-19
Have you tried using one of the other playback engines? Presumably you're using the gstreamer engine, can you get the arts or xine engines to work? (configure amarok->engine) - you might need to install them first though, if you havn't already ("sudo apt-get install amarok-engines" should get you a nice selection)

---

