---
title: "No sound with doom3 demo"
date: 2009-06-14
forum: Gaming &amp; Leisure
---

### Post by themusicalduck on 2009-06-14
When trying to run the doom3 demo I get this error message:

WARNING: failed to open sound device '/dev/dsp': Device or resource busy

WARNING: sound subsystem disabled

I've tried running the game with commands +set s_driver oss and +set_alsa_pcm pcm with no luck. I also applied the latest patch to the game with no difference.

If I change the sound driver to oss in the ubuntu sound settings there is no sound, and no sine plays when using test.

I also have two pieces of sound hardware, one onboard and one soundcard.

---

### Post by themusicalduck on 2009-06-14
bump

---

### Post by nolliecrooked on 2009-06-14
> **themusicalduck said:**
> When trying to run the doom3 demo I get this error message:

WARNING: failed to open sound device '/dev/dsp': Device or resource busy

WARNING: sound subsystem disabled

I've tried running the game with commands +set s_driver oss and +set_alsa_pcm pcm with no luck. I also applied the latest patch to the game with no difference.

If I change the sound driver to oss in the ubuntu sound settings there is no sound, and no sine plays when using test.

I also have two pieces of sound hardware, one onboard and one soundcard.

try taking out the soundcard.

---

### Post by themusicalduck on 2009-06-14
I'm using the soundcard at the moment. I could disable my onboard sound, but from the error message it doesn't look like it's what's causing the problem.

---

### Post by nolliecrooked on 2009-06-14
> **themusicalduck said:**
> I'm using the soundcard at the moment. I could disable my onboard sound, but from the error message it doesn't look like it's what's causing the problem.

try it anyway :P

---

### Post by themusicalduck on 2009-06-14
I disabled the onboard sound and now I can use the oss drivers from sound options. Though now doom comes up with a different error message.

WARNING: failed to open sound device 'dsp': No such file or directory

WARNING: sound subsystem disabled

Looking in /dev/ there is definitely a file named dsp. I tried setting DoomConfig to dsp1 with same result. I also tried setting it to /dev/dsp but got this error: WARNING: mmap 131072 bytes on device /dev/dsp failed: Input/output error

---

### Post by nolliecrooked on 2009-06-14
> **themusicalduck said:**
> I disabled the onboard sound and now I can use the oss drivers from sound options. Though now doom comes up with a different error message.

WARNING: failed to open sound device 'dsp': No such file or directory

WARNING: sound subsystem disabled

Looking in /dev/ there is definitely a file named dsp. I tried setting DoomConfig to dsp1 with same result. I also tried setting it to /dev/dsp but got this error: WARNING: mmap 131072 bytes on device /dev/dsp failed: Input/output error

take the sound card out of the machine, dont just disable it.

---

### Post by themusicalduck on 2009-06-14
I can't it's integrated onto the board. If I need to take out my actual soundcard which I am using now to get it to work.. Then I'd rather just use the soundcard and not bother with playing doom.

---

### Post by nolliecrooked on 2009-06-15
rofl.

dude take out the soundcard, and run on the intergrated chip.

---

### Post by themusicalduck on 2009-06-15
No xD

Screw it, it's wired up how I want it. I'm not gonna switch over to the integrated chip just to play one game!

Thanks for the help anyway man.

---

### Post by caravel on 2009-06-15
Important: Did you run Doom3 from the installer after finishing the install?

If so open a terminal and do the following:

```
sudo rm -r ~/.doom3
```

Close the terminal and open a new terminal.

Now run Doom3 again from this new terminal or run it from the menu.  Do not run it with sudo.

---

### Post by themusicalduck on 2009-06-15
I did run it after the install and fixed the permissions manually after I couldn't change resolution. Tried that command anyway, but sound still doesn't work. Error message says '/dev/dsp': Device or resource busy again.

I can't think of anything that would be occupying the soundcard. The only stream that is listed in PulseAudio volume control is System Sounds and I can't seem to terminate it. All my system sounds are disabled too.

---

### Post by themusicalduck on 2009-06-16
One more bump for this.

---

### Post by imaginaryboy on 2010-02-14
Finally figured this one out (with retail doom 3)

It works with alsa as the backend, if you use the right device.  Make sure ~/.doom3/base/DoomConfig.cfg has lines like:

seta s_driver "alsa"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_pcm "default"

Also, you should get the same results if you run speaker-test with the same device; i.e. before now, my file had seta s_alsa_pcm "surround40"

pts/5:0:~/.doom3/base>speaker-test -Dsurround40
Playback open error: -16,Device or resource busy

You can get a list of devices with "aplay -L" but since speaker-test worked fine with the default, even with 4 channels, I just used that one.

I've only seen this with Doom 3 & Karmic;  It was fine on intrepid, and ioquake, quake4, Prey, etc. all seem fine on Larmic.

---

