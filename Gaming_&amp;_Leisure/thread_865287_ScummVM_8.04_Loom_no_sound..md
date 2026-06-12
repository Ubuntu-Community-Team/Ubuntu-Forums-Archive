---
title: "ScummVM 8.04 Loom no sound."
date: 2008-07-20
forum: Gaming &amp; Leisure
---

### Post by Cellwind929 on 2008-07-20
I've been trying to figure out how to get sound working in ScummVm for the game Loom. I have my track1.wav file, which I tried converting to .flac and .ogg with audacity. No luck. I must be missing a setting somewhere. I think pulse audio might have something to do with it. I tried default audio and alsa audio settings in Scumm. I have no clue what to do to get it working. Any help would be appreciated.

---

### Post by FranMichaels on 2008-07-21
Hmm, I think I can help.

It should be Track1 not track1 :)

As for converting wav to flac (which I did too) the easy way is to go to the folder in terminal, and type

```
flac *.wav
```

Works great if you are dealing with multiple tracks (or in my case too lazy to type the track name.) :D

If you prefer a GUI way, go to Add/Remove and grab Sound Converter.

---

### Post by Cellwind929 on 2008-07-21
I already converted it to flac, I also tried Ogg, neither worked. I also tried Track1 and track1, neither work. I'm pretty sure this is a pulse audio problem.

---

### Post by FranMichaels on 2008-07-21
Within Scummvm, click Options, Audio, and try changing the music driver. 

Do you get sound in other scumm games? Try flight of the amazon queen or Beneath a Steel Sky, which are in the Ubuntu repos.

---

### Post by Cellwind929 on 2008-07-21
Welp, I got it working, with absolutely no clue what I did, just playing around with the files. The speech file works great now. Thanks for the help Fran.

---

