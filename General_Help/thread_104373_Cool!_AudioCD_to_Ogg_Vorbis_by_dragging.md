---
title: "Cool! AudioCD to Ogg Vorbis by dragging"
date: 2005-12-16
forum: General Help
---

### Post by jobezone on 2005-12-16
Hi, I switched to Kubuntu a few hows ago, and I had forgot this cool thing from KDE.
I inserted an AudioCD, and opened it in konqueror. Aside the various tracks, there were folders named "CDA", "Flac", "Full CD", "Information", "MP3" and "Ogg Vorbis". I dragged the "Ogg Vorbis" one to my home dir, and it seems to be converting the audiocd to oggvorbis right now.
Will see how it ends up.

---

### Post by ltmon on 2005-12-16
It's a pretty nice feature, and between audiocd:/ and fish:/ the best features of the kde ioslave framework are shown.

It's damn slow though... using command line tools I can rip and encode a CD more than twice as fast.  Not sure where the overhead is coming from.

L.

---

### Post by jobezone on 2005-12-16
What app do you use to encode AudioCD's to Ogg Vorbis? Just found out one slight nuissance of doing this, the names aren't renamed (Track 01.ogg, etc.)

---

### Post by GoldBuggie on 2005-12-16
Strange...mine retrieves the info from cddb. I guess you have kdemultimedia-kio-plugins installed since it has the libkcddb1 package which retrieves from cddb. Even when only browsing the CD I got the files tagged correctly.

you can look in how they are tagged at kcontrol->sound & multimedia->AudioCD

Also maybe the "konqueror->settings->configure konq.->Previews & Meta data" local protocols effects what is shown. Try and enable some there. apps, systems, audiocd those might be important.

---

### Post by jobezone on 2005-12-16
ah, the CD is was using was a custom made AudioCD, that's probably why it didn't fetch better names... Still have to try with a comercial CD, though..

---

### Post by Chris Tucker on 2005-12-16
is there a way to preserve song data on burned cds so that systems know the names of the songs without using CDDB? ive seen it happen once, with half a cd.... but i dont know how or why, i think it was just a fluke. and will never happen again..

---

### Post by jobezone on 2005-12-16
Perhaps that was using the musicbrainz or simillar databases?

---

