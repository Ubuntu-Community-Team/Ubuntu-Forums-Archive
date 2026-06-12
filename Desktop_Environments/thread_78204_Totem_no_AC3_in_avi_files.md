---
title: "Totem no AC3 in avi files?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Titan3025 on 2005-10-18
Hi,

I am having difficulties playing AVI files with Totem when the sound is encoded in AC3. I tried both totem versions (totem-gstreamer, totem-xine).

Totem refuses to play them and complains about audiodevice busy.

cya
Titan3025

---

### Post by Ugeek on 2005-10-22
Install gstreamer-a52 package... xine should work.

---

### Post by Poul on 2005-10-25
got same problem here
After installing breezy i installed totem-xine and w32codecs
I remember that at that point I was able to play ac3 files but movies with standard encoding (mp3) had no sound. Then i installed all gstreamer plugins to sort it out and now every time when i try to play ac3 file the error pops up
"audio device is busy. Is another application using it ?"

---

### Post by Titan3025 on 2005-10-25
exactly the same here!!! 

I installed all gstreamer-plugins and finally tried totem-xine.

I also get the "audio device is busy. Is another application using it ?" error message :-(

---

### Post by Titan3025 on 2006-03-15
any updates on this topic?

---

### Post by cerdiogenes on 2006-06-02
In Ubuntu Dapper you must install gstreamer0.10-plugins-ugly.

---

