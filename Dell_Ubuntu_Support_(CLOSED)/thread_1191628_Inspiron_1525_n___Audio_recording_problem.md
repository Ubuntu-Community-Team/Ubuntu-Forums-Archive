---
title: "Inspiron 1525 n   Audio recording problem"
date: 2009-06-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by newIsle on 2009-06-19
Hey all, 

I've been trying to record some audio with audacity from FireFox as it plays...(not stealing, from an open source "Philharmonia orchestra site"..check it out)... I'm trying to record through the headphones into the mic jack..(through the output into input jacks)

anyway my problem is I cant distinguish between all the options in the alsaMixer... in the record tab theres six option for volume levels, capture 0, 1, 2, also Mux 0, 1, 2.. (also by default the little mic icons are all disabled by default whenever i open the alsa mixer,.. every time)

  Then in the options tab of the mixer there are more options like,  

IEC958 playback source;--1)Digital playback, 2) ADAT, 3) Analog Mux 1,2,3

*Digital Input Source;--1)Digital mic 1,2)Digital Mic 2, 3)Analog inputs

and finally; three separate of this option;

Input source;-1)mic, 2)front mic, 3)line

there are three jacks at the front on the notebook two for headphones and one for a mic

I should mention that there is a mic that works when I use skype, but i dont know if thats called the front mic or digital mic,, theres alot of options here that i dont quite understand 

I'm running Jaunty 9.04 on Inspiron 1525 n series, kernel is 2.6.30rc
the audio device is listed as ;
82801H (ICH8 Family)HD audio controller STAC9200 Codec, Sigmatel 9205

i'm not sure what the problem(actually i do, its me) but I'm guessing it the settings, and what devices i choose to do the recording 

any help would be great, thanks

---

### Post by newIsle on 2009-06-19
Also while in audacity, it gives me several options for a recording device;
ALSA; HDA Itel:STAC92xxAnalog(hw:0,0)
ALSA; Pulse
ALSA; Default
OSS: /dev/dsp

don't know if thats relevant or not. :)

---

### Post by keraba on 2009-06-19
I have an XPS M1530 and this is what I've found.

The "digital" mic is the pair of mikes around the webcam, while the front mic is the jack in the front of the laptop.

To experiment, what I do is run alsamixer in one xterm, and in another xterm run:

arecord | od -x | grep 000

Now, what you can do it adjust stuff in alsamixer and see if it produces anything from arecord. When you see random gibberish, you know you're recording. If you see lots of 7f7f and 8000 or the display doesn't move at all, then its not receiving anything.

To get the "digital" mic to work, what I had to do was, in alsamixer, on the *playback* "screen", flip input source to digital, and on the capture "screen", flip the first input source from "front mic" to "mic".

Hope it helps.

---

### Post by gradinaruvasile on 2009-06-19
Open alsamixer in a terminal. Make a screenshot by pressing alt+PrintScreen. Press tab - your view changes to the capture view. Make a screenshot of that too and post them here.

---

### Post by newIsle on 2009-06-19
[http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-newislenewisle-laptop-1.png]("http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-newislenewisle-laptop-1.png")

[http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-newislenewisle-laptop-2.png]("http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-newislenewisle-laptop-2.png")

heres those screen shots...

---

### Post by astrakhan on 2009-08-27
thanks for the advice guys! I've been struggling with this for so long now.

this is what finally works for me:

Sound Preferences: 
Everything Autodetect except
Devices -> Audio conferencing -> Sound capture: PulseAudioSoundServer
Devices -> Default Mixer Tracks -> Device: Playback HDA Intel - STAC92XX Analog (Pulse..)

Alsamixer (commandline version):
Under 'All' tab:
1st capture -- [100%]
1st input      -- [Mic]
1st Mux       -- [50%]
Digital Input Source: ANALOG INPUTS

followed keraba's advice and checked out "arecord | od -x | grep 000" also tested with sound recorder and skype. i found that Digital Input Source must be set to ANALOG INPUTS for anything to happen.
oh yeah in skype, you can then set input source to pulse audio.

this works for dell 1525 with just front mic (no webcam/ mic combo) running dell's version of jaunty -- what did dell actually do to the generic release? the audio was still totally busted after install! bah...

---

