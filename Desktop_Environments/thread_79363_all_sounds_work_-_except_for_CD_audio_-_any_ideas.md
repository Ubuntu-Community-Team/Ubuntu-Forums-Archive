---
title: "all sounds work - except for CD audio - any ideas?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by bionnaki on 2005-10-20
hello. breezy detected my soundcard and I can hear all system sounds as well as play media (mp3, movies, ogg, etc) - sound works just fine everwhere. I am unable hear any sound when I try to play a cd with CD Player, Grip, and Beep Media Player. The tracks show up & it looks like it is playing, but there is no sound.

I cannot figure out why this would be...any ideas? Thanks!

---

### Post by migueljacq on 2005-10-20
[QUOTE=bionnaki]hello. breezy detected my soundcard and I can hear all system sounds as well as play media (mp3, movies, ogg, etc) - sound works just fine everwhere. I am unable hear any sound when I try to play a cd with CD Player, Grip, and Beep Media Player. The tracks show up & it looks like it is playing, but there is no sound.

I cannot figure out why this would be...any ideas? Thanks![/QUOTE]

I had the same problem. Whilst this is not a solution to the problem, I instead use soundjuicer to play my cds. The audio works in there but for some reason not cd player.

---

### Post by bionnaki on 2005-10-20
hey, that works for me too. good to know...thanks
although I'd like to know why there is no cd-audio
in the other apps....

hmm.

---

### Post by migueljacq on 2005-10-20
[QUOTE=bionnaki]hey, that works for me too. good to know...thanks
although I'd like to know why there is no cd-audio
in the other apps....

hmm.[/QUOTE]

logic would suggest these certain apps aren't detecting the soundcard, but I wouldn't know how to fix it :(

---

### Post by bionnaki on 2005-10-20
true...

---

### Post by ember on 2005-10-20
Hmmm ... I guess it's an issue with digital and analog sound playback. I suppose you connect your CD-Rom drive with your soundcard - at least, that fixed all issues for me in Warty.

Best,
ember

---

### Post by YanH on 2005-10-20
I had this problem in Hoary Hedgehog. This was due to my machine not having a cable connecting the CD ROM player to the Soundcard. The sound worked in Windoze because it was extracting the audio and playing it using Software rather than directly playing the CD audio. I installed the Cable and CD Audio worked fine :).

---

### Post by CencioPeravolos on 2005-10-23
[QUOTE=bionnaki]hello. breezy detected my soundcard and I can hear all system sounds as well as play media (mp3, movies, ogg, etc) - sound works just fine everwhere. I am unable hear any sound when I try to play a cd with CD Player, Grip, and Beep Media Player. The tracks show up & it looks like it is playing, but there is no sound.

I cannot figure out why this would be...any ideas? Thanks![/QUOTE]
No ideas, but a similar problem.
Sound works just fine everwhere.
I've got problems only when i play a cd with  CD Player or Sound Juicer: The music is reproduced "jerkily".
If I play cd with xmms or grip it's all good.
Have it to do with gstreamer ?

---

### Post by celian on 2005-11-20
Had same problem, all sound worked (mp3, dvd,) all basic codecs etc.

But when playing an audio cd, no sound, no matter what application I tried using (gnome-cd, xmms, cdplay (cdtools), totem etc..).

Then I found a solution (partial) here: [http://www.eglug.org/node/1644](http://www.eglug.org/node/1644)

**_Resume_**

For XMMS:

1. Under Preferences, select "I/O plugin": CD Audio Player  1.2.10 (libcdaudio.so)

2. Press "Configure".

3. Change the "Play mode" from "Analog" -> "Digital".


Now Audio-CD playback should work, but only with xmms.. Other apps don't seem to have a similar setting..

Hope this helps someone else!

- Celian

---

