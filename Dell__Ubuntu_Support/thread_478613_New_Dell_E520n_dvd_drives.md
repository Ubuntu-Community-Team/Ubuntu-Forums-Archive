---
title: "New Dell E520n dvd drives?"
date: 2007-06-19
forum: Dell  Ubuntu Support
---

### Post by luckyd on 2007-06-19
I just got my new Dell and I love it... except for when I am trying to watch movies. I bought it with the the dual cd/dvd drives, so both of them have the capability to play dvds. When I put a movie in, Totem immediately begins playing it, but when I close Totem and try to play the movie later, it says it does not have the appropriate plugins to play the dvd. GXINE and MPLAYER both send out approximately the same error messages. When I run a dvd in vlc, and specify the correct directory of the dvd, it plays but with many stops and starts. (VLC's problem) Is there a way to get any of the previously mentioned players to play a dvd on my computer, I have all of the restricted codecs needed to play dvds. What's going on? :confused:

---

### Post by apel_2804 on 2007-06-19
maybe this will fix your problem:

[http://www.tbaumi.de/blog/?p=8](http://www.tbaumi.de/blog/?p=8)

---

### Post by luckyd on 2007-06-19
Nope :(

---

### Post by apel_2804 on 2007-06-19
was there a ubuntu update before the problem happend? is the dvd drive working fine?

---

### Post by luckyd on 2007-06-19
Yes the dvd drive is working fine otherwise, and there was ubuntu update, but the drive didnt work before either.

---

### Post by c_eric_ray on 2007-06-20
The ultimate ubuntu multimedia setup...

Dowload Automatix II and install all the multimedia codecs and dvd authoring tools. This process will add all the software and codecs you need to play dvds. Most importantly, totem-gstreamer will be _uninstalled_ and totem-xine will _installed_ in its place. When this is done you'll be able to open to move later (if you close totem and leave the dvd in the drive)

Uninstall totem-mozplugin and install mplayerplugin-in. This gives you more support for a wider variety of streaming and internet based multimedia capabilities. 

For Flash support make sure you have flashplugin-nonfree installed.

Using this combination I there's nothing on the web that I can't view, stream, or listen to.

Good luck.

---

