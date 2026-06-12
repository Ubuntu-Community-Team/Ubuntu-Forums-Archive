---
title: "amarok stopped working after EasyTag install"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mad_phoenix on 2005-12-09
Hi,
  I was happilly using amarok in my new Ubuntu install until for no apparent reason it stopped being able to play mp3's.  It complains that gst-engine cannot play mp3, even though it did before.  Also, rhythmbox (which also uses gstreamer-engine) functions just fine with mp3's.  
  I tried running gst-register-0.8 both as user and root, no difference.  Ive installed the gstreamer08-plugins-multiverse, so I'm pretty positive it should be working.  The only change I made that could've broken this is installing EasyTag, but it didn't even install any dep's to go with it, and removing EasyTag didn't change anything.
  This is really frustrating, has anybody else had a similar experience or have any advice to offer?  Thanks!

PS as a side note, what is the default audio engine for Ubuntu?  It seems like I keep seeing OSS everywhere...is this really the default?  Isn't ALSA built into the kernel these days?

---

