---
title: "Getting MIDI to work, and &quot;properly configureing ALSA&quot;."
date: 2005-03-31
forum: Desktop Environments
---

### Post by Ricapar on 2005-03-31
I'm following this HOWTO:
[http://ubuntuforums.org/showthread.php?t=8736](http://ubuntuforums.org/showthread.php?t=8736)

I followed everything it said there, and it's not working, but I'm pretty sure I know why. When I did [FONT=Courier New]lsmod[/FONT], the ones the guy said were supposed to be there weren't. 

I have an onboard card, so I'm using FluidSnyth. When I ran [FONT=Courier New]fluidsynth -m alsa_seq ./ultimate.sf2[/FONT], I got this:

```
cca_open_socket: could not connect to host 'localhost', service '14541'
cca_init: could not connect to server 'localhost' - disabling ladcca
ALSA lib pcm_hw.c:1155:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
fluidsynth: error: The "default" audio device is used by another application
Failed to create the audio driver
``` 
And I think that's being caused because of the above problem.

I've looked around, but I haven't seen a FAQ or HOWTO on how to "properly configure ALSA". Help me please  :(

---

### Post by jazzer on 2005-04-01
Having not actually tried MIDI in Ubuntu yet, I can only guess using the log you provide.  It states that another application is using the sound device; in all likelyhood you will need to disable the 'esd' daemon (enlightenment sound daemon - a software mixer) from starting up when GNOME starts up.  You can disable that by going to 'Computer' -> 'Desktop Preferences' -> 'Sound' and uncheck 'Enable Sound Server on startup'.

Do note when you disable the 'esd' sound daemon you will no longer be able to play multiple sources of audio at once.  Hopefully this helps.

---

### Post by Ricapar on 2005-04-01
I just tried that, and I got the same error again :(

If it helps, the system says that my sound card is:
"VIA 82c686A/b rev50"
and the chip is:
"Cirrus Logic CS4299 rev 4"

I got both of those from the ALSA Mixer

---

