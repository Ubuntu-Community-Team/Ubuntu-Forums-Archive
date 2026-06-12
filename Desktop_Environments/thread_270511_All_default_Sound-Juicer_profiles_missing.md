---
title: "All default Sound-Juicer profiles missing"
date: 2006-10-03
forum: Desktop Environments
---

### Post by earth_walker on 2006-10-03
Hi all,

I just put a cd into my drive, and sound-juicer complained that "the currently selected audio profile is not available on this system". When I clicked 'change profile', it only offered one named 'wav' with nothing in any of the fields. In other words, the default Ogg and Wav profiles have disappeared (it's been about a month since I tried to rip a cd on this computer, so I have no idea what could have happened to delete these profiles).

I've tried reinstalling sound-juicer and all the gstreamer plugins, to no avail. I've searched around, and all the posts I can find on this tells how to add an MP3 profile rather than how to restore the default Ogg Vorbis and Wav.

Could someone please post their settings (pipes) for each default setting please? Is this indicative of something else broken?

Thanks in advance

---

### Post by Paerez on 2006-10-04
I am also having this issue. I am on Edgy, though.

---

### Post by clawhound on 2006-10-05
Fortunately, I have a second install of Ubuntu.

Profile Name: CD Quality, Lossy
GStreamer Pipeline: audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

File Extension: ogg

---

### Post by clawhound on 2006-10-06
Hasn't solved it. btw.

---

