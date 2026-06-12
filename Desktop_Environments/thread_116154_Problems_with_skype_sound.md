---
title: "Problems with skype sound"
date: 2006-01-12
forum: Desktop Environments
---

### Post by manie.coetzee on 2006-01-12
Hi, I'm running Kubutu Breezy badger 5.10.  

I've installed Skype (1.2.0.18), and I can make my first call to the Echo server (sound and microphone works).  The problem comes in when I try and call somebody for the second time.  It then indicates to me that there was a sound error.  If I close Skype, and open it up again, I can again just make one call.  I have enabled full duplex mode, and selected the ALSA audio device.  

Anybody have an idea where to start looking?

---

### Post by paulmilliken on 2006-01-12
[QUOTE=manie.coetzee]Hi, I'm running Kubutu Breezy badger 5.10.  

I've installed Skype (1.2.0.18), and I can make my first call to the Echo server (sound and microphone works).  The problem comes in when I try and call somebody for the second time.  It then indicates to me that there was a sound error.  If I close Skype, and open it up again, I can again just make one call.  I have enabled full duplex mode, and selected the ALSA audio device.  

Anybody have an idea where to start looking?[/QUOTE]
I have had the same problem.  Perhaps you can try an older version of skype?  I will make another post if I get it working.

Paul

---

### Post by manie.coetzee on 2006-01-12
I think the must have something todo with multiple applications using the sound infrastructure at the same time.  Maybe there's a .soundrc file that somebody have, that will configure the stuff correctly?

---

### Post by Zhukov on 2006-01-13
I believe i have a solution! Testing it now! Stand by for an how to :)

---

### Post by Zhukov on 2006-01-13
See this:

[http://ubuntuforums.org/showthread.php?p=653625](http://ubuntuforums.org/showthread.php?p=653625)

Hope it works for you!

---

### Post by manie.coetzee on 2006-01-14
Hi, thanks for all the feedback.  I'm running Kubuntu (KDE), and don't know if the setup will work for me.  In the meantime I've found a little script/program called 'skype_dsp_hijacker'.  It get's the job done.  If I disconnect from a call, it reset some sound stuffies, so that it's available again.  I will use this script until skype has implemented native ALSA support.

---

