---
title: "what is a good dvd player program"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Andrew12106 on 2006-07-12
i cant play dvds with the default program

---

### Post by scxtt on 2006-07-12
i like good ol' Xine (0.99.3) [package xine-ui] myself ... not totem, totem-xine or mplayer or VLC, etc. ...

don't forget about libdvdread ...

---

### Post by taurus on 2006-07-12
Which default program are you talking about here?  You can always try vlc, xine, mplayer, etc.  Of course, you need to install all the necessary apps before you can play a DVD.  Use Automatix to do that then...

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by Andrew12106 on 2006-07-12
how would i go about getting xine?

---

### Post by scxtt on 2006-07-12
you can use synaptic to search for it or **sudo apt-get install xine-ui** in a terminal should work nicely ...

i'm using ver. 0.99.3 (from breezy) instead of 0.99.4 because the latest version was flat out ignoring my specified codec directory ...

---

### Post by Andrew12106 on 2006-07-13
when i type that in the terminal it cant find the package, do i have to enable some other repo?

---

### Post by Andrew12106 on 2006-07-13
i installed totem-xine but it says i need libdvdcss

---

### Post by Andrew12106 on 2006-07-13
nevermind, problem solved :D

---

### Post by scxtt on 2006-07-13
xine-ui is in the universe repository ...

in /etc/apt/sources.list:
[indent]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse[/indent]

---

