---
title: "Jaunty and some sound issues. . ."
date: 2009-05-15
forum: General Help
---

### Post by CAUSTICROUTER on 2009-05-15
Hey guys,  I have had kubuntu installed on my computer for quite some time.  I just recently upgraded to jaunty and I am enjoying it so far, except for a couple of sound issues I have been having.  I have an m-audio revolution 5.1 soundcard and I have got it working fine with amarok (with pulse audio)  My issue is that sound in firefox (youtube,  flash, etc) does not work at all.  I have read countless threads on people with similar issues,  but none of the solutions seemed to work. I have flashplayer 10 installed(from the adobe site) and I am pretty sure I have that evil flash package uninstalled.  Sound worked in firefox for awhile,  then I changed a bunch of things (not sure to what extent,  took me a couple hours) to get surround sound working (comment out a line in the pulseaudio config file is finally what fixed it) and the sound in flash stopped working altogether.  I installed flashplayer 10 and the sound started working again,  but then I restarted and it quit working.  I have reinstalled flashplayer 10, but it has not helped.  The other problem is that I cannot play more than one stream at once.  This is very annoying,  because when (when flash sound worked) I wanted to listen to a music video on youtube or watch something,  I would have to exit amarok, restart firefox,  and watch the video.  Thanks in advance for the help.

---

### Post by gettinoriginal on 2009-05-15
Here is a good site to try:
[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html)
:p

---

### Post by CAUSTICROUTER on 2009-05-15
Thank you very much.  I added the users and root to the pulse groups and now sound in flash works.  I still can't play sound from two programs at once,  but I can live with that until I fix it.  Thanks again.

It seems as I fix one problem,  I only cause another.  I updated alsa to 1.0.19 and now sound works in both applications,  at once.  BUT, now surround sound does not work.  I had my computer set up to replicate the front channels and send them to the rear when listening to music,  but I don't remember how I did it.  I think it has something to do with a custom .asoundrc but I can't be sure.

Surround sound works,  in alsamixer,  the center and rear channels were turned all the way down.  Thanks for everything.

---

### Post by hutxubix on 2009-05-31
Yes, running kubuntu jaunty with the same problem, adding root and users to the pulse audio groups fixed the problem

---

### Post by downclimb on 2009-06-10
I hope to have found the easiest solution of all - open up Kmix and turn your PCM sound up.  ;)

---

