---
title: "Sound Juicer weirdness"
date: 2006-04-23
forum: Desktop Environments
---

### Post by Nikusan on 2006-04-23
Hi all, 

Tracks that I've ripped to mp3 at 192kbps with Sound Juicer all have really huge durations (~17 minutes for a ~3 minute song). They appear to Rythmbox as 32kpbs but they're clearly not... I assume this is why the duration is being calculated so wrong. When I slide the slider in rythmbox past the actual ending of a track it starts playing some other song in the same directory.

When playing them in Totem the duration starts at the high number and comes down as the track progresses.

Finally, I'm pretty sure they're all CBR as apposed to VBR.

So, what the?

---

### Post by bennyj on 2007-07-08
I know this is an old post...but I am having the same exact problem. I get realy long time lengths on the mp3 i rip,So big that I can not burn a cd with serpentine without it telling me that I am exceding the  capacity of the cd with just 12 songs.Does any one have a solution to this. I am using the latest SoundJucier with my pipeline set as follows
```
 audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux
```

thx

---

