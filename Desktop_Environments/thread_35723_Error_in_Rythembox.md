---
title: "Error in Rythembox"
date: 2005-05-20
forum: Desktop Environments
---

### Post by bdmp on 2005-05-20
When I play an mp3 file in Rythembox I get an error, "Error: Could not open resource for writing" and then "Could not pause playback" How do I fix this?

---

### Post by bored2k on 2005-05-20
[QUOTE=bdmp]When I play an mp3 file in Rythembox I get an error, "Error: Could not open resource for writing" and then "Could not pause playback" How do I fix this?[/QUOTE]
 Rhythmbox is probably trying to use the eSound client. Problem is, KDE chokes it by locking the ARTS sound client. You can go to kcontrol and make KDE use esound, but that is not recommended. Plus, amaroK is IMO better than Rhythmbox..

---

### Post by bdmp on 2005-05-20
I can use amorak but the sound is all clicky. Sounds like a record. How can I fix that?

---

### Post by bdmp on 2005-05-22
Yeah, so i went with amorak and I fixed the clicking by going to (in kubuntu) The K --} control center --} Sound and multimedia --} sound system --} hardware ---} select sound system ---) choose Open Sound System.   

Hope this helps someone.

---

### Post by ollyshaw on 2005-06-14
I had problems with rhythmbox after a kubuntu install. was getting errors such as, cant open media for writing, etc. I fixed this by running gstreamer-properties as root and selecting open sound server as the input. Hey presto rhythmbox works a treat!

Olly

---

