---
title: "mp3"
date: 2005-12-26
forum: General Help
---

### Post by phil123 on 2005-12-26
Is there a special way of opening mp3 and mpg files? My Totem rection is  "there are no decoders" and "you may need to install the coresponding plugins". Can somebody point the way forward? Cheers
Phil.

---

### Post by pharcyde on 2005-12-26
When you say open mp3/mpeg files, how do you want this to be done?  Through what program?

mp3/mpg can be played through mplayer.
mp3 can be played through xmms which is a winamp clone.

---

### Post by irv on 2005-12-26
I just put my mouse pointer over a MP3 file in my home folder and it starts playing. I am not sure what I did to make this happen, but I like it that way.

---

### Post by SavageBeginner on 2005-12-26
You need to install w32codecs: [http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)

I recommend installing totem-xine.  Totem-gstreamer is still being developed and has some bugs with video.
```
sudo apt-get install totem-xine
```
It should work fine after that.

---

### Post by phil123 on 2005-12-27
My Breezy installation includes Totem, Rhythm Box and Serpentine but none of them seem to want to play mp3 or mpg. Shouldnt one of these play these files without too much complication?
Phil112233

---

### Post by cstudent on 2005-12-27
mp3 codecs aren't free software so they are not included in Ubuntu by default. You can add them yourself. I suggest using the Automatix package to install the ability to play just about all media you will come across.

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

