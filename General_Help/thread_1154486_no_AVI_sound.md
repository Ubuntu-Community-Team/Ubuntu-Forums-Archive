---
title: "no AVI sound"
date: 2009-05-09
forum: General Help
---

### Post by sandyd on 2009-05-09
I recently reinstalled Ubuntu (instead of upgrading to jaunty), and ive installed ubuntu-restricted-extras.

HOwever, i can't get any sound when playing avi videos. NONE. at all.

other video formats have sound

what am i missing?

---

### Post by mb_webguy on 2009-05-10
An avi is just a container, which can contain a number of different types of audio formats.  Since you're only encountering sound problems with certain media files, I'd suggest using [MediaInfo]("http://mediainfo.sourceforge.net/en") to identify the audio contained in the files.  This will make it much easier to identify the problem.

---

### Post by sandyd on 2009-05-10
> **mb_webguy said:**
> An avi is just a container, which can contain a number of different types of audio formats.  Since you're only encountering sound problems with certain media files, I'd suggest using [MediaInfo]("http://mediainfo.sourceforge.net/en") to identify the audio contained in the files.  This will make it much easier to identify the problem.

seems that ALL audio formats in an AVI container don't play. Tried encoding with mp3 (im sure i have the mp3 codec b/c/ i can play mp3s) mpg... everything. no sound.

---

