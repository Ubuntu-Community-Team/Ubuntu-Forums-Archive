---
title: "Sound Juicer/Transcoding Questions"
date: 2005-12-18
forum: General Help
---

### Post by nmatheis on 2005-12-18
Hello
I keep an ever-increasing music collection on an external hard drive.  I'm in the process of switching over to Linux from Windows and have a dual-boot desktop system with Win2k and Ubuntu.  When preparing for ripping cds on Ubuntu with Sound Juicer, I can't see where to change the flac and ogg quality settings.  I'm used to using EAC/Foobar for ripping/transcoding.  I usually rip to Wavpack and then transcode to ogg at q6.  My questions are...

Can I (easily) configure Sound Juicer to rip to Wavpack?

Can I change the ogg quality settings to use 192 nominal vbr (aka q6)?

What programs can I use to transcode Wavpack/Flac --> Ogg?

Thanks!
Nikolaus

---

### Post by silverfire on 2005-12-18
I don't know all the details and am fairly new to Ubuntu, but I just took a look around Sound Juicer and there's a button that reads "Edit Profiles" right next to the box where you choose FLAC/Ogg Vorbis/WAV. Clicking on that brings up another window where you can edit, add or remove the format profiles. Editing the OGG one brings up these options: Profile Name, Profile Description, GStreamer Pipeline, File Extension and a checkbox for Active or not active.

Taking a look at the GStreamer Pipeline, it looks like it contains encoding quality information: " audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5"

Is this what you're looking for, in part at least?

---

### Post by nmatheis on 2005-12-18
after searching a bit more extensively, it looks like the gstreamer setting for sound juicer off encoding has the quality setting of 0.5, which another thread here said equals q5.  further, the thread i found said that the quality settings in the gstreamer configuration range from 0 - 1, equaling q0 - q10. so, i'm goin to change it to q6 and be happy with that!

---

### Post by bionnaki on 2005-12-18
I really like soundconverter for converting lossless to lossy (usually flac to ogg). I recommend it. 

also, have you seen this script: [http://www.ubuntuforums.org/showthread.php?t=82806&highlight=flac](http://www.ubuntuforums.org/showthread.php?t=82806&highlight=flac) ?

---

