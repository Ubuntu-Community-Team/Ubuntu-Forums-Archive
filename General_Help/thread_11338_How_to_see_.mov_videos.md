---
title: "How to see .mov videos"
date: 2005-01-16
forum: General Help
---

### Post by Benko on 2005-01-16
Hi I've got a digital camera wich olny takes .mov movies.

But up to now I didn't succed in seeing them with Totem.

What can i do for that ?

---

### Post by poofyhairguy on 2005-01-16
[QUOTE=Benko]Hi I've got a digital camera wich olny takes .mov movies.

But up to now I didn't succed in seeing them with Totem.

What can i do for that ?[/QUOTE]


Install Xine and new codecs:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Adrenal on 2005-01-16
[mplayer](http://www.ubuntuforums.org/showthread.php?t=9850)

---

### Post by macewan on 2005-01-16
straight xine or mplayer is probably the best route but you sound like you want gui environment that is close to desktop. Find some codecs from the mplayer server below.

[http://ftp5.mplayerhq.hu/mplayer/releases/codecs/](http://ftp5.mplayerhq.hu/mplayer/releases/codecs/)

I've got mine extracted in ~/.gnome2/totem-addons

sudo apt-get install totem-xine

This works for me - mileage may vary

---

