---
title: "Doom 3 Alsa Problems"
date: 2006-12-26
forum: Gaming &amp; Leisure
---

### Post by aglc2005 on 2006-12-26
I have been searching around the forums for a while now trying to get the solution for this problem. Now I have read to switch doom 3 over to oss, but I have absolutly no sound with oss, everything runs through my Alsa driver, but in Doom 3 the alsa driver gives off this real grable sound. Any help would be nice.](*,)

---

### Post by pay on 2006-12-26
Look here [http://ubuntuforums.org/showthread.php?t=15722](http://ubuntuforums.org/showthread.php?t=15722) and here [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/) and try install oss. I think it's called aoss on ubuntu.```
sudo aptitude install aoss
```

---

### Post by aglc2005 on 2006-12-26
Ok, after reading the first forum post I think I understand what is wrong with my setup, how ever I do not know where the DoomConfig.cfg file is, the only file I know of is /usr/local/games/doom3/doom3 for configuration. I do indeed have oss installed, its alsa-oss. One thing I noticed is that in my volume control I have two different devices

0: NVidia Ck804 (Alsa mixer)
1: Realtek ALC850 rev 0 (OSS Mixer)

However, the Realtek mixer does not provide ANY option besides Speaker and four capture option and I have no sound throughout the system when using that mixer.

---

### Post by jagwah on 2006-12-26
Your Doom3 config file will be in your home/yourname/.doom3/base folder, it is called 'DoomConfig.cfg'

---

### Post by aglc2005 on 2006-12-27
Ok, here is what my config file has set

```
seta s_dsp "/dev/dsp"

seta s_driver "oss"

seta s_alsa_lib "libasound.so.2"

seta s_alsa_pcm "default"
```

edit: Also here is the error I am getting:

------ OSS Sound Initialization ------
WARNING: failed to open sound device '/dev/dsp': Device or Resource Busy
WARNING: sound subsystem disabled

---

### Post by pay on 2006-12-30
Make sure that you have anything making sound turned off.

---

### Post by rajeev1204 on 2006-12-31
hi
try this for doom3 /quake 4

run it like this ./doom3( or whatever is the run file)  +set s_driver oss


This will surely work.Let me know .


regards

rajeev

---

### Post by aglc2005 on 2006-12-31
> **rajeev1204 said:**
> hi
try this for doom3 /quake 4

run it like this ./doom3( or whatever is the run file)  +set s_driver oss


This will surely work.Let me know .


regards

rajeev

Hi, this is what I get for running it with that code

```
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe

```

However, I cannot get the game to boot now, even without adding the +set s_drive oss.

```
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()

```

I have just recently installed XGL so that I may run Beryl, could this have a conflict? I tried turning Beryl off and switched back to Metacity, but everything results the same.

---

### Post by MetalMusicAddict on 2006-12-31
Did you run Doom3 from the installer after the installation was finished?

---

### Post by rajeev1204 on 2007-01-01
hi

Beryl is beta and also i believe dangerous !! I never use beta stuff .

Anyway here is something else for sound

 ./(gamerunname)             +set snddriver ao +set snddevice oss  ( Actually its for quake 2 ! but try it anyway though i recommend my first fix)

This should do it. If not come back here. Also remember ,**very important what pay said, turn off anything else using sound **, for example ur rythmbox applet on pause or something like that. 

Then try my first solution and then if no luck the second one.  I type again **./doom3(whatever) +set s_driver oss**.

I think when u first typed that command u may have something related to sound in background.

I too have a realtek sound card . So try selecting that.


regards
rajeev

---

### Post by fakie_flip on 2007-01-22
> **aglc2005 said:**
> Hi, this is what I get for running it with that code

```
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe

```

However, I cannot get the game to boot now, even without adding the +set s_drive oss.

```
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
------ OSS Sound Shutdown ------
close sound device
--------------------------------
idRenderSystem::Shutdown()

```

I have just recently installed XGL so that I may run Beryl, could this have a conflict? I tried turning Beryl off and switched back to Metacity, but everything results the same.

Did you get sound to work? I have the same sound card devices you mentioned. Maybe your motherboard is the same as mine. I have a NS1 SLI Lite made by ECS.

---

### Post by aglc2005 on 2007-01-31
Actually I am having even bigger problems right now, I had to reinstall everything on my computer including ubuntu. Now I cannot get and sound channels other than my left and right to work. But my board is an Abit KN9, but it is very possible that we have the same card if you have nForce 4

---

