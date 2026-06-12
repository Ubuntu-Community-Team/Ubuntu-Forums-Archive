---
title: "How to concatenate mp3 files?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Captain Rotundo on 2006-06-09
I have a directory full on mp3s I would like to combine into a single long mp3 file, what is a good way to do this?

---

### Post by matthew on 2006-06-09
open a terminal

navigate to the directory where the mp3 files are e.g. " cd /home/username/mp3"

type "cat file.mp3 song.mp3 music.mp3 > bigfile.mp3"
where the mp3s are listed in the order in which you want them concatenated

or

if all the mp3s are numbered/named in order e.g 1.mp3, 2.mp3 or a.mp3, b.mp3 then you can just "cat *.mp3 > bigfile.mp3"

---

### Post by Captain Rotundo on 2006-06-09
Would this work? the files arent purely audio stream they have things like tags in them, wouldn't that screw up the audio at the transition?

---

### Post by doonium on 2006-06-09
one way to do it is to decode the mp3s to wav, join the wavs, then encode the wav to mp3.

to decode, you can use lame (lame --decode blah.mp3), but now i think you'd have to use toolame.  

then, you can use quelcom's tool (apt-get install quelcom) qwavjoin to join the wav files together.

then, use lame (lame blah.wav) or toolame once again to encode the resulting wav to an mp3.

---

### Post by matthew on 2006-06-09
[quote=Captain Rotundo]Would this work? the files arent purely audio stream they have things like tags in them, wouldn't that screw up the audio at the transition?[/quote]Good question...I've done it with varied success with mpgs and other files but I honestly didn't think about the tags...try the other poster's idea as it seems to effectively address this problem.

---

### Post by aysiu on 2006-06-09
[*mp3wrap* is a good program for this.](http://www.ubuntuforums.org/showthread.php?t=141178&page=2)

---

### Post by Captain Rotundo on 2006-06-09
I think mp3wrap may do it.  I wanted to avoid decoding and re-encoding, to preserve what little quality these mp3s have (they aren't very high quality as it is). Thanks for the help.

---

### Post by BoyOfDestiny on 2006-06-09
[QUOTE=Captain Rotundo]I think mp3wrap may do it.  I wanted to avoid decoding and re-encoding, to preserve what little quality these mp3s have (they aren't very high quality as it is). Thanks for the help.[/QUOTE]

I imagine if you just tar it (not tar.gz) as one file, that would work... I'm gonna test that and see...

Edit: it works, just rename it to .mp3

---

### Post by Jose Catre-Vandis on 2007-07-25
> **matthew said:**
> open a terminal

navigate to the directory where the mp3 files are e.g. " cd /home/username/mp3"

type "cat file.mp3 song.mp3 music.mp3 > bigfile.mp3"
where the mp3s are listed in the order in which you want them concatenated

or

if all the mp3s are numbered/named in order e.g 1.mp3, 2.mp3 or a.mp3, b.mp3 then you can just "cat *.mp3 > bigfile.mp3"

This works just fine :)

---

