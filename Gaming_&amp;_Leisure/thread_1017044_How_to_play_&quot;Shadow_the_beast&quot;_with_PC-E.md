---
title: "How to play &quot;Shadow the beast&quot; with PC-Engine ? (ISO)"
date: 2008-12-20
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-12-20
Hello,

 I would like to play PC-Engine. So with Shadow the beast game
(it's a cdrom /iso)
 
Here there is the emulator, deb of the emulator:
[http://www.zeograd.com/dl.php?arg=308](http://www.zeograd.com/dl.php?arg=308)

Is there anyone that understand what we should do to play this console?:(:(

---

### Post by frenchn00b on 2008-12-20
1-So to make it:
check the config of mednafen, it needs a syscard3.sys file to be "pathed"

2-convert all mp3/ogg to wav
 
3-mednafen *.cue

Enjoy !

[Solved]

---

### Post by FranMichaels on 2008-12-21
Mednafen supports iso and ogg or flac, just modify the cue sheet, change WAV to VORBIS.

---

### Post by frenchn00b on 2008-12-21
> **FranMichaels said:**
> Mednafen supports iso and ogg or flac, just modify the cue sheet, change WAV to VORBIS.

and concering MP3, shall I always convert them from mp3 to wav ?
or I can modify the cue too, but WAV cannot remain in the cue ... :confused:

---

### Post by KingHanco on 2008-12-21
When you download those cd rip games. Some have the tools that convert mp3 or ogg to wav. Please beware some of those games are missing parts or bad rips.

So far I found a few that isn't playing right or missing parts or doesn't play at all. I went ahead and deleted those.

I have over 10 PC-Engine cd games.:lolflag:

---

### Post by frenchn00b on 2008-12-21
> **KingHanco said:**
> When you download those cd rip games. Some have the tools that convert mp3 or ogg to wav. Please beware some of those games are missing parts or bad rips.

So far I found a few that isn't playing right or missing parts or doesn't play at all. I went ahead and deleted those.

I have over 10 PC-Engine cd games.:lolflag:

Well I would be bit ashamed to use wine/dosbox, because we have linux, it's easier to convert sounds:
```
#!/bin/sh
for i in *.mp3 ; do echo "------------------" ;  echo   " converting `basename "$i" .mp3`".wav "$i"  ;   mpg123 -w "`basename "$i" .mp3`".wav "$i"     ; done
```

So we've got to have Wav. Pitty that mednafen/gens dont use the mp3, that would save some space a bit ;)


Which pc-engine games do you like?

---

