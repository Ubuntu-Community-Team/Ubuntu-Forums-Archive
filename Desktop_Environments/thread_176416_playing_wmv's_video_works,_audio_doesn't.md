---
title: "playing wmv's: video works, audio doesn't"
date: 2006-05-14
forum: Desktop Environments
---

### Post by s0ad on 2006-05-14
Hi.  I just installed Breezy Badger.  After the installation was complete, I made sure all the applications were up-to-date.  Now I'm trying to play some video files.  I've tried vlc,xine,totem and the video works perfectly in all.  But the problem is with audio.  I can't hear a damn thing.  I'm using a usb Logitech Headset.  I've been searching around the forums for probably and hour hour-half, and I've tried some things, but nothing has worked.  So if someone could please help me, I would appreciate it very much.

---

### Post by Sef on 2006-05-14
Have you downloaded the codecs?

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by s0ad on 2006-05-14
I've done this ([http://makuchaku.info/amnesty/#codecs)](http://makuchaku.info/amnesty/#codecs)).  I also downloaded w32codecs, although I had to get the tar.gz version instead of the .deb package because the Archive manager would not read the .deb.  I browsed to /usr/lib/codecs and /usr/lib/w32 and both folders have the same files.

---

### Post by DarkStarDeity on 2006-05-14
I found the answer to the same problem here: [http://ubuntuforums.org/showthread.php?t=25668](http://ubuntuforums.org/showthread.php?t=25668)

---

### Post by s0ad on 2006-05-14
I tried editing the .cache file, and changing the priority from "1" to "7", but it failed to solve my problem.

---

