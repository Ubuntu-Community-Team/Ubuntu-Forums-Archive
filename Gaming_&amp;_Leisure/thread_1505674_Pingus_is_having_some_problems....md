---
title: "Pingus is having some problems..."
date: 2010-06-09
forum: Gaming &amp; Leisure
---

### Post by Goomby on 2010-06-09
Hello!

I seem to be having at least two problem with the game, Pingus.


[LIST=1]
[*]The audio doesn't work perfectly, in that the instruments seem to be the main problem.  I'm not hearing all the instruments when I was playing the game. I used to be able to hear them when I played Pingus back on 9.10 (I use 10.04 now)
[*]Pressing F5 does open the option menu, but I can't click on anything.  However it's not completely frozen as I can still exit out of the program, and put it to full screen.
[/LIST]
Any help?  I've tried uninstaling followed by reinstalling and restarting the computer, nothing changed.

---

### Post by ShadowMage on 2010-06-09
Hey there,

Regarding the audio issue, there is a bug report here: [https://bugs.launchpad.net/ubuntu/+source/pingus/+bug/575319](https://bugs.launchpad.net/ubuntu/+source/pingus/+bug/575319)

I know this doesn't solve your problem but, I don't think there is a solution yet. At least not that I know of. Out of curiosity, are you using 64-bit Ubuntu?

---

### Post by Goomby on 2010-06-10
Thanks for the info.
Also, no I'm using 32-bit.

---

### Post by Jthulhu on 2010-10-17
Me and my son play and edit levels in Pingus all the time and I recently had this problem manifest itself(missing sound channels).

I'm guessing it is an sdlmixer bug but can't prove it.
Anyways this is what I did about it.

I copied the music from the pingus data folder
 /usr/share/games/pingus/data/music

They are all Impulse tracker files(*.it & *.s3m) which are kind of like midi.
I converted them to .wav files using an application called Schism Tracker(in the ubuntu repository).
Then I converted the wav files to ogg vorbis(.ogg) using Audacity.

Then using sudo Nautilus in terminal I copied the .ogg files back to /usr/share/games/pingus/data/music

Then I used sudo gedit to edit all the .pingus files in /usr/share/games/pingus/data/levels/tutorial and /usr/share/games/pingus/data/levels/holloween and replaced all the ".it" in the data with ".ogg"(minus the quotes)

The music works fine now.
Hope this helps.

---

