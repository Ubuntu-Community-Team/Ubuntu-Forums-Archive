---
title: "rip audio from a dvd"
date: 2005-11-13
forum: Desktop Environments
---

### Post by manicka on 2005-11-13
I need a tool to rip audio from a dvd

suggestions?

---

### Post by bionnaki on 2005-11-13
thoggen - I played around with it once & was able to rip an .ogg audio file

---

### Post by matthew on 2005-11-13
[quote=bionnaki]thoggen - I played around with it once & was able to rip an .ogg audio file[/quote]That's a pretty cool little program, but it seems to rip dvd's into ogg/theora ***video*** files, not ogg ***audio*** files.

I am also interested in this question. I have a lot of concert dvd's I would love to be able to listen to in my car, etc.

---

### Post by Remmelas on 2005-11-14
doesn't mplayer have a --dump-audio option that could be used?  It's been to long since i've used it, but may fit the bill for you.

---

### Post by vasdee on 2005-11-14
i did exactly this with a program called transcode. Unfortunately its command line based but there is a gui for it called dvd::rip - however i've never used it. 

I found a really good website that helped me through the commandline options but i'm having a bit of trouble re-googling it right now :???:

---

### Post by bionnaki on 2005-11-15
in windows, you'd use dvd decrypter to rip the dts stream. so, get dvd decrypter working thru wine...and rip...and convert.

---

### Post by flaming_monkey on 2005-11-15
Good old mplayer to the rescue.

Ensuring you have libdvd and mplayer installed, find the chapter you want to rip.
```

$ mplayer dvd://1
$ mplayer dvd://2
$ mplayer dvd://3 ... etc.

```

Once you've found the chapter you want to rip use the following options:

```

$ mplayer dvd://1 -vc dummy -vo null -af resample=44100 -ao pcm:file=ripped-audio.wav

```

The output .wav file can then be compressed with lame or oggenc

```

$ oggenc -q4 ripped-audio.wav -o ripped-audio.ogg

```

---

### Post by RikoW on 2005-11-15
I did the same a few days ago, since I have some music DVD with live concerts I want to put on my portable mp3 player.

I use acidrip (in the repos) to extract .avi files from the DVD. I find acidrip much easier to use than dvdrip for example. Also, it seems to be faster for that above purpose, if I'm not mistaken.

from the avi files, you can then extract the audio files using ffmepg:

```
ffmpeg -i chapter1.avi chapter1.mp3
```

However, I found that the mp3's created with ffmepg play fine on my computer, but my ipod refuses to play them. So, I extract .wav instead analogous to the above line and then convert .wav to .mp3 using lame:

```
ffmpeg -i chapter1.avi chapter1.wav
lame chapter1.wav chapter1.mp3

```

Good luck,

    Riko

---

