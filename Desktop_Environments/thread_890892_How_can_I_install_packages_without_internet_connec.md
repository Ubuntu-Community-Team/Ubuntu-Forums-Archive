---
title: "How can I install packages without internet connection?"
date: 2008-08-15
forum: Desktop Environments
---

### Post by stot on 2008-08-15
I'm submitting this thread as an addendum to [http://ubuntuforums.org/showthread.php?p=936161](http://ubuntuforums.org/showthread.php?p=936161)

I currently do not have (nor do I want) internet at home.  However, I recently installed Kubuntu on a Shuttle XPC desktop at home.  Kubuntu appears to have a very elegant package installer, which I have used to install Samba, XMMS, and Opera.

Unfortunately, I have not gotten DVD playback to function yet.  In Freespire Linux, DVD's play ok in Kplayer after installing libdvdcss2.  But Kubuntu uses Kaffeine instead of Kplayer.  After I installed libdvdcss2 in Kubuntu, DVD's still will not play in Kaffeine.  I also installed kubuntu-restricted-extras_15_i386.deb, but to no avail.  Is this a library issue, or is this a Kaffeine issue?

---

### Post by phidia on 2008-08-15
You may need other packages to get fully usable playback. Check out [this guide]("http://ubuntuforums.org/showthread.php?t=766683") from the multimedia & Video Forum. 
You probably need to get a interent connection temporarily (bring the computer to a friend's place that has it)?

---

### Post by stot on 2008-08-22
I attempted to install gstreamer, kmplayer, kplayer (mplayer), and vlc.
At some point kaffeine accidentally got uninstalled.
I tried reinstalling it, and DVD's play in Kaffeine now!
Also, they play a lot better in Kaffeine on Kubuntu 8.04 than I've seen them play in Kplayer on Freespire 2.0.
I'd like to post exactly which dependencies I installed with it, but there are 51 of them so I'll have to get around to it later.

---

### Post by mailtwogopal on 2008-08-22
Hi stot,

  Its better to have internet connection temporarily to get updates in ur pc.

---

