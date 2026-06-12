---
title: "Retaining game sound while playing mp3s in Quake3"
date: 2007-10-31
forum: Gaming &amp; Leisure
---

### Post by employeeno5 on 2007-10-31
Hey there everyone.
I just spent a long while working to get sound running in Quake 3 (the game was otherwise running top notch). 
I've got the sound and everything running together now. 
I finally went to sit down and play a bit only to discover that if I have mp3s playing before I start Quake3, the music will keep playing fine, and the game will play fine, but I'm back to no in-game sound.  If I'm not playing music when the game starts the in-game sound still loads fine of course.
I'm hoping there's some manner in which I can be playing music and still get the in-game sound to load when I start-up the game. 
I'm just using the rhythmbox player for music. I don't know if another player would be better suited for this, though  I'm guessing it wouldn't make a difference. 
If anyone has any ideas that would be fantastic. 
Thanks!

---

### Post by employeeno5 on 2007-11-01
To provide some more information on the problem, I, like many many people it appears, could not immediately get sound working on my linux install of Quake 3. 
I had a message during loading saying that it could not mmap my /dev/dsp file. I tried many things such as making sure that quake's .cfg was pointing to the correct /dev/*dsp* file (it was) and changing permissions and ownerships on the file. 
In the end the only thing that has worked for me is running these commands before the game.
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

Now, I have my sound working, but if I'm listening to mp3's I again lose the in-game sound. It appears that currently I must chose between one sound or the other; I may not have both together.

If I'm already playing music on my desktop, again in-game music won't play because (according to the terminal) /dev/dsp is busy/already in use by another device, a predictable message.
I've tried changing all my sound settings to ALSA and then all  OSS and various combinations in between, which I didn't expect to really change anything (it didn't). 

I'm not really sure where to start to allow for music and in-game sound. I also don't know if the nature of my initial sound fix is part of what's preventing me from accomplishing this, or if it would have been an issue anyways. I'm almost more interest at this point in learning if/how to fix this as part of my further education into using linux, rather than just getting the sound to my ideal preference.

Many thanks if anyone has any ideas/solutions.

---

### Post by cogadh on 2007-11-01
You probably have a sound card that is not capable of hardware mixing, meaning that only one audio stream at a time will actually play. You might be able to configure ALSA for software mixing, which should allow multiple streams, though with some latency (depending on processor and sound card). There are instructions on how to do that here:
[http://alsa.opensrc.org/index.php/Hardware_mixing%2C_software_mixing](http://alsa.opensrc.org/index.php/Hardware_mixing%2C_software_mixing)

I can't be much more help than that, I've never been able to really get it working on my system and ended up accepting the either game sound or music option.

---

### Post by employeeno5 on 2007-11-01
I'm at work right now, but I look forward to checking out the link later. I don't suppose the fact that I could play both both sound sources in windows means anything does it?  (I'm brand new to Linux if it's not completely obvious.)
Thanks for the advice!

---

### Post by cogadh on 2007-11-01
Unfortunately, Windows handles sound much better than Linux at the moment. It can handle multiple audio streams natively, no matter what your sound card is. For example, my SB Audigy LS, which is really nothing more than a re-labeled SB Live! 5.1, handles surround sound and multiple audio streams quite well in Windows but had huge problem with surround sound and couldn't run multiple streams at all in Linux. If you have a card that is capable of hardware mixing (higher-end cards), then this is generally not a problem.

---

