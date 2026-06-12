---
title: "WMA files not playing nor converting"
date: 2005-11-14
forum: Desktop Environments
---

### Post by hamil on 2005-11-14
I have got a bunch of WMA's that I would like to listen to..
Thought that it would be no challenge for my Ubuntu machine...

First I tried to get Beepplayer to play them, but it will not even load it into the playlist. Downloaded the xmms-wma plugin, and took it as a sure ting that xmms would play it, but no... It starts the track, but you can only hear approxematly 1 sec of choppy sound, before it jumps to the next track..
Well, I figured, since I do not like the wma files, I could try to convert them to my file of choice, ogg.
The closest I came, was a script that would convert it to mp3 for my. Fair enough...
I made sure taht I had installed mplayer, lame and everything, went to:
[LinuxQuestion](http://www.linuxquestions.org/questions/answers/352) and followed that guide.

When I run this script, my WMA's is deleted, and replaced by a mp3 file with a file size of 4.9 KB.

Anyone now what happens and why? I am not able to here any sound at all in my new mp3's

My output, for one of the files in terminal is:
```

MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for Debian.


-waveheader is deprecated. Use -ao pcm:waveheader instead.
LAME version 3.96.1 (http://lame.sourceforge.net/)
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 17249 Hz - 17782 Hz
Encoding audiodump.wav to 02_spor_2.wma
Encoding as 44.1 kHz 128 kbps stereo MPEG-1 Layer III (11x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA
     8/10     (80%)|    0:00/    0:00|    0:00/    0:00|   4.1796x|    0:00
average: 128.0 kbps   LR: 11 (100.0%)

Writing LAME Tag...done
ReplayGain: -12.8dB

```

---

### Post by Kyral on 2005-11-14
Conversion isn't the way to go. Try the steps outlined here

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by hamil on 2005-11-14
I do have all of the codecs and everything else listed on that page.
But I am not able to listen to any of those files anyway..

When i run the *.wma file in xmms from the terminal, I get this output:
```

Message: device: default
Message: fmt 5, channels: 2
Message: alsa mixer timed out

```

And just when Message: fmt 5, channels:2 is visible in the terminal, I hear this maybe one second chopping.

---

### Post by Kyral on 2005-11-14
Whoa...then its not a problem with the WMAs...its something with ALSA

---

### Post by hamil on 2005-11-14
Hmmm...
I have tried to change between ALSA, OSS and eSound in xmms, but no luck with any of them... The same thing happens, regardless of which one is selected. Only a brief choppy sound.

---

### Post by Hairy_Palms on 2005-11-14
its a problem with beep-media-player, the xmms plugin doesnt work. for beep u need a special plugin, get it from [http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-extras/](http://seveas.ubuntulinux.nl/dists/breezy-seveas/breezy-extras/)
then install it with dpkg

---

### Post by hamil on 2005-11-14
Grrrrrrrrrrrr... :)
Well, I downloaded this plugin, and installed it. So now beep is also able to open the *.wma files and put it in the playlist. But still, no one is able to play the full length tracks. Beep also only plays a very short choppy sound. I have no other sound troubles, but this wma thing...

---

### Post by Hairy_Palms on 2005-11-14
if thats the case then its not a problem with xmms or the player as kyral said, its probably something to do with your soundcard and soundserver, try changing your sound server in the menu "System->Preferances->Multimedia Systems Selector"

---

### Post by hamil on 2005-11-14
Nope...
Not helping that either...
Changed to OSS and ESD, but nothing there..
I am able to lisen to normal MP3's, OGG's, wav's and other soundfiles, but just not my wma files...

---

### Post by poptones on 2005-11-14
Did you by any chance make these WMA files yourself? 

My bet is they are encrypted and can only be played on the OS installation that created them. Have you tried playing them on another windows machine?

---

### Post by hamil on 2005-11-14
Yes, those files are ripped by windows mediaplayer on another machine. 
Is it not possible to open them because of that??? Is not wma wma?
Will try to reboot into windows later tonight, and test them there.

---

### Post by poptones on 2005-11-14
Nope, this is a "feature" Microsoft puts in the windows media player. There is a little checkbox hidden in the preferences that says something like "protect my media files." This means "encrypt my media files so they can ONLY BE PLAYED ON THIS MACHINE. 

Microsft sets this as default. If you do not know to change it, you will only rip *encrypted files*. 

Nice feature, huh?

---

### Post by Hairy_Palms on 2005-11-14
if they are ripped by wmp then they will be encrypted with a load of drm crap.

---

### Post by hamil on 2005-11-14
:shock: :twisted: WTF????

Well, I should have seen it coming... :) What a nice little feature to put into their programs... Hate....

Well nothing to do... Easyer to rip the cd's one more time then, with Sound Juicer this time...
I am not going to forget this Bill!!!

Thanx for the help guys! Now I actually knows that my mediaplayers will play every file I will ever get my hands on, except some *.wma files...

---

