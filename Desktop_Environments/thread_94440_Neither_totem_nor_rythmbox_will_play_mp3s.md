---
title: "Neither totem nor rythmbox will play mp3s?"
date: 2005-11-24
forum: Desktop Environments
---

### Post by linuxNewb on 2005-11-24
Everything worked fine in hoary. I did a clean install of breezy, apt-getted w32codecs from a repo given on another thread. But neither totem nor rythmbox will play mp3s. What's wrong? Thanks in advance.

---

### Post by aysiu on 2005-11-24
You don't need w32codecs to play MP3s. You need lame.
Find anything with the word *lame* in it here:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by NeoChaosX on 2005-11-24
Actually, he needs gstreamer0.8-mad to play MP3s in both programs (assuming he's got the default totem-gstreamer package installed).

---

### Post by Ugeek on 2005-11-24
If you have default totem(gstreamer) use gstreamer-mad package.
    sudo apt-get install gstreamer0.8-mad
it will also activate rhythmbox's mp3 play.
you can also use totem-xine but then rhythmbox wont play mp3.

cheers

---

