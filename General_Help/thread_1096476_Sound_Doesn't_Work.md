---
title: "Sound Doesn't Work"
date: 2009-03-14
forum: General Help
---

### Post by Kissell on 2009-03-14
My sound will work if I reboot.  But after awhile it stops working.  

When I go to SYSTEM / PREFERENCES / SOUND and try to play a test, it says: 

> 
audiotestsrc wave=sine freq=512 ! 
audioconvert ! audioresample ! 
gconfaudiosink: Could not open audio device for playback.


But then if I reboot it works fine again.  

I'm about to re-install Ubuntu from scratch, unless someone can help me fix this problem, it has become very inconvinient/annoying.

---

### Post by emarkay on 2009-03-15
FWIW, see this post - similar but different but still audio issue.

[http://ubuntuforums.org/showthread.php?t=1080767](http://ubuntuforums.org/showthread.php?t=1080767)

---

### Post by Yumi on 2009-03-15
Following this threat solved it for me after trying everything.

[http://ubuntuforums.org/showthread.php?t=997506&highlight=alsa+icon]("http://ubuntuforums.org/showthread.php?t=997506&highlight=alsa+icon")

You could also upgrade to Jaunty. It is only alpha but seems already better than Intrepid (for me anyway).

Michael

---

