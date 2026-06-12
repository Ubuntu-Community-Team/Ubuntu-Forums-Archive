---
title: "Weird Problem with Notifications"
date: 2009-11-04
forum: Desktop Environments
---

### Post by The-NightPhoenix on 2009-11-04
There is some kind of weird bug in my notifications 

the notification is supposed to show from the upper side but it is shifted like there is another notification above it.

the only notification that starts in the original place is the sound notification

Screenshots attached

this problem only appeared in Karmic Koala 9.10
but it worked very well b4.

i think it might be cuz of a problem in the sound . cuz i also have some wierd things going with the sound.

---

### Post by fenrir12 on 2009-11-04
I have this same problem. I don't think it is anything to do with sound though, I'm pretty sure it is something in the notify-osd package.

---

### Post by sherington on 2009-11-04
Believe it or not, this is by design.

There's a long thread on it somewhere where Mark Shuttleworth explains the rationale.

---

### Post by Theory5 on 2009-11-04
Yea its supposed to be like that, when you adjust volume or screen brightness on a laptop there is a window that pops up in the usual place. But for things like pidgin and song notifications it pops up lower. Its been annoying me so I found this:
[http://blog.mahboy.com/archives/248](http://blog.mahboy.com/archives/248)

---

### Post by The-NightPhoenix on 2009-11-04
Thanx "Theory5"  Thats solved it. 

Solution at : [http://blog.mahboy.com/archives/248](http://blog.mahboy.com/archives/248)

Download the old notify-osd:

32:
[https://edge.launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1_i386.deb](https://edge.launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1_i386.deb)

64:
[https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1_amd64.deb](https://launchpad.net/~gilir/+archive/updates/+files/notify-osd_0.9.24-0ubuntu2~gilir1_amd64.deb)

---

