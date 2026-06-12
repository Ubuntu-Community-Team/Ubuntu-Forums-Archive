---
title: "Sound-Juicer won't rip .ogg files"
date: 2006-06-22
forum: Desktop Environments
---

### Post by gerkin on 2006-06-22
I have been unable to rip CD - .ogg files in a new install of Dapper, and I assume that others may be having the same problem;

After a bit of hunting the problem is caused by a leading space (" ") before the command: "audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5! oggmux"

see: Sound Juicer > Format > Edit Profiles > CD Quality, Lossy > Edit > GStreamer Pipeline: (then remove the leading space at the start of: "audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5! oggmux") & click "OK"

I hope this helps .......cheers :-\"

---

