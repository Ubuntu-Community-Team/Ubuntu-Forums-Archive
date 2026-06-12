---
title: "DOSBox - No sound"
date: 2008-04-25
forum: Emulators
---

### Post by Comreak on 2008-04-25
So far, I've tested out Blood and Ultima Underworld in dosbox.  Both games run, I just don't hear any of the music or sound effects.

I've got midi setup and working on my system with timidity.  And I've also added timidity's port number (128:0) to dosbox.conf so that I don't get any errors when starting up dosbox.  Sound works fine everywhere else in Hardy.

---

### Post by Comreak on 2008-04-26
Hmm, still haven't found any solutions.  (Hope it's alright if I bump this thing before it falls into forum oblivion.)

---

### Post by Comreak on 2008-04-27
Out of curiosity, I installed Xubuntu 8.04 and tried out Dosbox, and the sound worked right off the bat.  I can't imagine Xubuntu and Ubuntu being that different (maybe they are), so I was probably having issues because I started with Ubuntu 8.04 RC and then upgraded to the final via the updater.  

Whatever the case, everything is working now.  Not the best solution, if you want to stick with Ubuntu.

---

### Post by Vertelemming on 2008-05-11
I can't guarantee this is the same problem, but it worked for me when I had DOSBox sound problems on upgrading from Gutsy. In Synaptic, find "libsdl1.2debian-all" or "libsdl1.2debian-pulseaudio" and mark either one for installation. It may prompt you to uninstall "lbsdl1.2debian-alsa", but that's okay, go right ahead.

---

### Post by imaginal on 2008-05-12
Installing either of the two packages worked to get sound for me, but I get very strange bleeps and pauses that were not suppose to be there. When I close the game window, I get 
> DOSBox stdout> ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
DOSBox stdout> MIDI:Opened device:oss

Any guesses?

---

### Post by Vertelemming on 2008-05-14
Again, no guarantees that I'm accurate, but a lot of people have been complaining about the way PulseAudio buffers its audio, creating stutters, bleeps, odd static, and other issues. With DOSBox taking up CPU cycles to trigger the buffer under-runs, I would put good money on this being the problem.

I think there are instructions floating around on the forum on how to disable PulseAudio and return to using ALSA, but I'm not sure where. Be warned that it's a bit of a complicated process, to get it fool-proof.

---

### Post by jharkn on 2008-05-28
When I switched to using pulseaudio dosbox lost all sound, installing libsdl1.2debian-pulseaudio and removing libsdl1.2debian-alsa as per Vertelemming worked, though I've also got the bleeps and random noises mentioned above :/

---

### Post by MasterProg on 2008-07-08
Worked for me. As for now, I have no problems with PulseAudio. Thanks.

---

### Post by Pixman on 2009-11-13
[COLOR="Red"]PROBLEM HAS BEEN SOLVED!
[/COLOR]

For documentation purposes:
I saw, that in dosbox 0.73 some variables in the configuration file changed so that my configuration file didn't read it correctly.
So I started dosbox from an empty directory, used
```

config -writeconf dosbox.conf

```
and saw the following lines in dosbox.conf:
```

mpu401=intelligent
mididevice=default
midiconfig=128:0


```
Works properly now. :)

----------------------
Hello folks,

I'm "upping" this thread once again since a lot of people seem to have problems with sound in dosbox 0.73 again after the upgrade to karmic.

I have t he following configuration:
mpu401=intelligent
device=oss
config=128:0
(I've listed the ports of timidity, freepats are installed, the configuration should be correct)

but when I start dosbox, on the console I can find those two lines:

```
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss

```

I wouldn't care for it, since it says it uses OSS and previously it worked with this message, too, but then, the sound doesn't work AT ALL.

I just get no output. I tried various khz rates but I don't think the problem is there, since there isn't even any stuttering.

Could anybody recommend me a solution for this?
Should I try to compile my own version perhaps? I doubt it, since alsa midi support is compiled into the binary package from karmic.

Help is appreciated. :)


Greetings,
Pix

---

### Post by ProDigit on 2010-01-09
Same issue on Xubuntu 9.10
It used to work on openttd, but after manually configuring and doing make of a newer .deb file, my effects disappeared too (the midi player still worked).
I now installed dosbox, and there I have no sound.
VLC and mplayer have sound.

I think it's something inconsistent with the sound drivers.

---

### Post by ProDigit on 2010-01-09
Never mind!
I found the issue!
It's like mentioned above, to install "libsdl1.2debian-all"

it seemed pulseaudio gave me some trouble

Happy Dossing around! :D

---

### Post by bssdvr on 2010-05-28
In case someone still have this problem: ```
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:oss
```

I found a solution: you have to change ```
mididevice=default
```to```
mididevice=oss
```This solve the problem as dosbox was trying alsa before oss, and I have pulseaudio so alsa is not working.

---

### Post by curts on 2012-05-07
Any recommendations for 12.04?  The package "libsdl1.2debian-all" doesn't exist and "libsdl1.2debian" says it includes PulseAudio drivers.  I have the music running reasonably smooth in 'Pro Pinball - Timeshock!', but no voice or sound effects.

---

### Post by Perfect Storm on 2012-05-08
This is an old thread. Please start a new one in our emulator forum, thanks.


Thread closed.

---

