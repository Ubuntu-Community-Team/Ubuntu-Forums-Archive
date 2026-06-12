---
title: "No audio in Mplayer"
date: 2005-05-18
forum: Desktop Environments
---

### Post by himuraken on 2005-05-18
Hi, I downloaded and installed Mplayer and the "all" codec package. Whether I am trying to play an .mp3 or a Quicktime video I get this error:

[COLOR=Red]Clip info:
 Title: Disposition
 Artist: Tool
 Album: Lateralus
 Year: 2001
 Comment:
 Track: 10
 Genre: Other
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Checking audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
AF_pre: 44100Hz/2ch/s16le
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [null] 44100Hz 2ch s16le (2 bps)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:   6.7 (06.6)  0.6%

MPlayer interrupted by signal 2 in module: play_audio
[/COLOR]

My sound card is the onboard Nforce2 audio that is on my MSI board. By the way I don't knowingly have any sound related applications open and sound works in everything else.

TIA,

Himuraken

---

### Post by Amarack on 2005-05-18
You should try to play it through a command to see if it might be the sound system in gnome getting in the way. I would try using:

mplayer -ao esd filename

In the console to see if it gives you sound then. If so its just that mplayer is using the wrong audio output option, and that can be configured by changing the mplayer configuration file.

---

### Post by himuraken on 2005-05-18
Just wanted to add some further steps that I have done. From the command line I run: 
[COLOR=Red]mplayer -ao help[/COLOR]

and get:

[COLOR=Red]MPlayer 1.0pre7-3.3.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE


Available audio output drivers:
        mpegpes DVB audio output
        oss     OSS/ioctl audio output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output
[/COLOR]

Bearing in mind that I am newer to Linux than some, I can see that Ubuntu has defaulted my sound output/system to the Enlightened Sound Daemon, which is not in the list for "Available audio output drivers". Does this mean mplayer won't work on ESD?

---

### Post by himuraken on 2005-05-18
[QUOTE=Amarack]You should try to play it through a command to see if it might be the sound system in gnome getting in the way. I would try using:

mplayer -ao esd filename

In the console to see if it gives you sound then. If so its just that mplayer is using the wrong audio output option, and that can be configured by changing the mplayer configuration file.[/QUOTE]

I ran that from a command line (within Gnome) and got:

[COLOR=Red]Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)[/COLOR]

How can I boot Ubuntu without loading X initally so that I can try your suggestion without the X server running, I know CTRL ALT BackSPC reboots X, but how do you unload to try straight command line?

---

### Post by Amarack on 2005-05-18
You know, you might be able to test the playback out by just killing esd off and then trying to play the music.  Something like:

killall -9 esd
mplayer filename

---

### Post by himuraken on 2005-05-18
Thanks Amarack that did it, but now what are the negative affects of killing ESD and will it need to be done all the time? I am running mplayer primarily for quicktime and some mp3 work since everything I try to get XMMS to work without freezing has failed.

---

### Post by himuraken on 2005-05-18
Actually after killing ESD XMMS is working... Hrmm. Can I use OSS or something else? I am also not sure what the differences are.  I appreciate your help.

---

### Post by Amarack on 2005-05-18
First of all ESD does not need to be killed like that every time, if you choose not to use it. It can be disabled through the audio preferences (System->preferences...). I think the name is something like Start Sound Server.

But also, I think xmms can be configured to use esd so that if you are using it to play mp3s then you might not need to disable it in the first place. I have found that xmms freezing is quite common due to this problem. The directions for configuring xmms can be found here:

[http://www.ubuntuforums.org/showthread.php?t=29338&highlight=xmms+esd](http://www.ubuntuforums.org/showthread.php?t=29338&highlight=xmms+esd)

So you would select to use the ESD in xmms and that might get it working... 
As for mplayer the problem is the same thing, but I am still not sure what to do about it, because it seems like your mplayer does not have the esd output driver, very confused why it doesn't.

---

### Post by himuraken on 2005-05-18
OK I follow what you are saying. If I uncheck the box that says "enable sound server startup" will that cause playback issues after a reboot? Or does this just prevent Gnome from taken ownership of the soundcard at boot?

---

### Post by Amarack on 2005-05-18
It will stop using esd, but I think the down side is that system sounds might stop working. ESD takes over the sound output, so if you use esd you have to only use esd (as far as I know). Disabling it lets programs use sound directly, but it also means only one program can use sound at a time. Also, you would have the problem that things currently set to use esd would have to be set not to.

If you can get xmms and mplayer to use esd that may be better overall, but disabling esd all together works for some people just fine.

---

### Post by himuraken on 2005-05-18
Thanks for the help, I will try to live without ESD seeing as the system sounds aren't important to me at all. Thanks again.

---

