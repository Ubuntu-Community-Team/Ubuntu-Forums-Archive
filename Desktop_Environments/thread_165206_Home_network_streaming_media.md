---
title: "Home network streaming media?"
date: 2006-04-24
forum: Desktop Environments
---

### Post by dlai on 2006-04-24
Hello everybody me and my buddy have our own home network set up, and we woul really like to have the functionality of playing music on one computer and having the other playing the same music, through some sort of streaming that displays id3-tag information on the other computer.
Use-case:
My buddy sits in front of his computer using [Listen]("http://listengnome.free.fr/") Rhythmbox or amarok, and making his own playlist, when he push play, it instantly plays on his radio channel on my computer, whatever musicformat he plays. And when he changes the playlist it also changes on my computer.... Is this possible??
Hope somebody can enlighten me. Thanks in advance

---

### Post by KingBahamut on 2006-04-24
Ive always used Icecast. 

[http://www.icecast.org/](http://www.icecast.org/)

---

### Post by herridge on 2006-04-24
[http://www.slimdevices.com/su_downloads.html]("http://www.slimdevices.com/su_downloads.html")

While designed to work with the Squeezebox hardware, this software is great as a streaming music server.  You can control it through a java applet called Softsqueeze, in which case you can stream in flac lossless, or you can use a web interface and listen through any player that plays streaming mp3.

D

---

### Post by dlai on 2006-05-04
ok but do you know any good tutorials for setting up icecast?

---

### Post by louis_nichols on 2006-05-04
Amarok has a php interface. XMMS has such a plugin too. [MPD]("http://www.musicpd.org/") might also be for you.

---

### Post by dlai on 2006-05-04
Thank you but, I tried using the amarok interface but i dont know how to...and when using gnome, it could be really nifty to make the playlist from one computer graphically, and the other computer would just play on the fly... or something

---

### Post by louis_nichols on 2006-05-04
So basically you want one app with two command interfaces.

How about mpd then? they say it's pretty cool.

Would vnc or ssh be too much?

---

### Post by dlai on 2006-05-04
Ok this is begining to get a little weird i know... but maybe the best solution would be to have a shared file as the playlist, and a shared library, that should not be so hard, so if i set the other computer to play a playlist from a shared library, and i change it on the fly would that work, preferably through Rhythmbox and ssh... I'm not good at nfs

---

