---
title: "Sound Juicer MP3 Quality"
date: 2009-05-17
forum: General Help
---

### Post by bolter40k on 2009-05-17
I was ripping some cds into mp3 files but found out they arent that great quality how can i change this and what are te bit rates  i can input

here is the line i assume the quality seting is somewhere 
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```

what do i need to edit to raise the bit rate

-thanks

---

### Post by mc4man on 2009-05-17
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=[COLOR="Red"]6[/COLOR] ! id3v2mux

If you want to raise the quality then lower the number 6

The vbr  scale is 0-9. 0 being the highest quality, 9 the lowest.

Just change the number, gstreamer profiles don't respond well to bad edits

(don't consider this an endorsement of soundjuicer or any gstreamer based ripper/encoders, particularly for mp3

---

