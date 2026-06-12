---
title: "Rhythm box problums"
date: 2006-02-20
forum: Desktop Environments
---

### Post by tophat2445 on 2006-02-20
hi, I cant get Rhythmbox to play anything but .ogg files.... what can I do to fix this...

---

### Post by Qrk on 2006-02-20
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Postman on 2006-02-20
Try downloading 'Quod Libet' since it seems to play the MP3's from my Win98 system pretty well.  Get it at Add Applications/Music & Video section.

---

### Post by jbmalone on 2006-02-20
Quod Libet is awesome.  I don't think the repositories have the latest version though.

---

### Post by tophat2445 on 2006-02-20
I install Dapper Drake today...( I know I'm posting in a Breezy Badger section)...but In breezy...I had ALL the gstreamer plugins install, and was able to play .ogg, .mp3, .wma but now...I can only get Rhythmbox to play .ogg, but it will add mp3's to my library.....

I have ALL the gsteamer plugins installed on dapper too...:confused:

---

### Post by RAOF on 2006-02-20
Dapper's Rhythmbox uses gstreamer0.10, so you need all the gstreamer0.10 plugins.  Specifically: gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly should get you mp3 support.  (AAC/mp4 support is in gstreamer0.10-plugins-bad, and they're not in the repos yet).

---

### Post by tophat2445 on 2006-02-21
Ok, now I can get Rhythmbox to play .ogg, and mp3.  In Breezy, I could getRhythmbox to play .wma files but now I can't...what plugin do I need for that?

---

### Post by RAOF on 2006-02-21
[QUOTE=tophat2445]Ok, now I can get Rhythmbox to play .ogg, and mp3.  In Breezy, I could getRhythmbox to play .wma's what but now I can't...what plugin do I need for that?[/QUOTE]
Ba bauw!  I don't think you can - you would have been using the "gstreamer-pitfdll" plugin to load the windows .dlls which do the wma decoding (also known as the win32codecs).  I don't think that plugin has been ported to gstreamer0.10.

---

### Post by tophat2445 on 2006-02-22
haha, as of today, 2-22-05 I got an update...now, Rhythmbox will play my .wma files....YAY!

Huge thanks to the Ubuntu development team!

---

