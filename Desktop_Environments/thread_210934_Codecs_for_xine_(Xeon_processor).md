---
title: "Codecs for xine (Xeon processor)"
date: 2006-07-07
forum: Desktop Environments
---

### Post by ApuX on 2006-07-07
Hi,

I have a rare problem with the codecs for xine.

I'm using totem-xine and amarok with xine engine. I downloaded the codecs (all-20060501.tar.bz2) from [http://mplayer.ethz.ch/MPlayer/releases/codecs](http://mplayer.ethz.ch/MPlayer/releases/codecs),
extracted it, and move to /usr/lib/win32. But it doesn't work. If I try to play a mp3, totem show a error message and amarok just doesn't play the song.

I'm doing this in a computer with Xeon.

Note 1: I did the same in a Pentium-M and it worwks perfectly.
Note 2: I did a apt-get install libxine-extracodecs in the Xeon computer and now it works too (at least, with mp3), but it isn't exactly what I want, because I think the libxine-extracodecs are not as complete as the file downloaded (all-20060501.tar.bz2).

Does the codecs I downloaded have problems with Xeon or I did something wrong?
Have anybody had a similar problem with this (or other) processor?

---

### Post by ApuX on 2006-07-10
Ok, I'm not totally sure, but I've been testing something and I think that:

the all-20060501.tar.bz2, doesn't include "all" codecs. It doesn't include the mp3 one.
It's not a problem of the Xeon processor. The first time (pentium-m) I used aptitude, so the libxine-extracodecs were installed automaticaly. When apt-get is used, it doesn't install it by default, just suggest yo to do it. That's why I can mp3 in one istallation but not in the other one.

---

