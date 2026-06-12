---
title: "doom3 errors + quake 3 problem + sound problems"
date: 2005-09-30
forum: Gaming &amp; Leisure
---

### Post by aljones15 on 2005-09-30
Doom3 Demo loads but 

A. no text. it all appears as little boxes, but no actual writing

B. games crashes when it's about to start.
here's the error

43863 msec to load game/demo_mars_city1
idRenderWorld::GenerateAllInteractions, msec = 85, staticAllocCount = 0.
interactionTable size: 2819964 bytes
29897 interaction take 3348464 bytes
------------- Warnings ---------------
during game/demo_mars_city1...
WARNING: Couldn't load sound 'guisounds.wav' using default
WARNING: file def/weapon_bfg.def, line 102: Unknown entityDef 'damage_bfgSplash' inherited by 'damage_bfgsplash_cinematic'
WARNING: file def/weapon_bfg.def, line 92: Unknown entityDef 'damage_bfg' inherited by 'damage_bfg_cinematic'
WARNING: file def/weapon_bfg.def, line 97: Unknown entityDef 'damage_bfgFreq' inherited by 'damage_bfgfreq_cinematic'
WARNING: Unknown classname 'weapon_plasmagun' on 'weapon_plasmagun_1'.
5 warnings
signal caught: Aborted
si_code -6
Trying to exit gracefully..
--------- Game Map Shutdown ----------
--------------------------------------
idRenderSystem::Shutdown()
------------ Game Shutdown -----------
--------- Game Map Shutdown ----------
--------------------------------------
Shutdown event system
--------------------------------------
shutdown terminal support
andrew@alj:/usr/local/games/doom3-demo$


Quake 3 demo


root@alj:/home/andrew/Desktop # ./linuxq3ademo.gz.sh
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


and the actual .sh file generates a bunch of errors which i can't copy and paste
seem to be unknownt type errors


installed vlc and it works, but no sound


root@alj:/home/andrew/Desktop # wxvlc
VLC media player 0.8.1 Janus
[00000268] mpeg_audio packetizer: MPGA channels:2 samplerate:44100 bitrate:160
[00000291] mpeg_audio decoder: MPGA channels:2 samplerate:44100 bitrate:160
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
[00000293] oss audio output error: cannot open audio device (/dev/dsp)
/dev/dsp: Device or resource busy
[00000293] esd audio output error: cannot open esound socket (format 0x00001021 at 44100 Hz)
[00000293] arts audio output error: arts_init failed (loading the aRts backend "/usr/lib/libartscbackend.la" failed)

how do I detect my soundcard and get the driver's? ubuntu's defualt sounds works. using an Xnote LS50A

peace,
a

---

### Post by geekchic9 on 2005-09-30
You're posting 3 problems in a single post. Hmm. It would be better if you posted 1 at a time.

About the sound: Ok. Are you using Hoary? Because Hoary has sound issues and one of your problems is a sound issue. I would type into a terminal "killall esd" (maybe "sudo killall esd" if nothing happens) and then try running wxvlc again.

About the text: It's probably because a certain font isn't installed. Does Doom3 Demo come with any fonts? Maybe you could google how to install those fonts. Read the help files if the Doom3 people supplied them.

About the authentication error: You probably need to install some sort of protocol such as TLS or SSL or something like that. Again, read the help files if the Doom3 people supplied any.

I hope that helped a little.

---

### Post by aljones15 on 2005-09-30
[QUOTE=geekchic9]You're posting 3 problems in a single post. Hmm. It would be better if you posted 1 at a time.

About the sound: Ok. Are you using Hoary? Because Hoary has sound issues and one of your problems is a sound issue. I would type into a terminal "killall esd" (maybe "sudo killall esd" if nothing happens) and then try running wxvlc again.

About the text: It's probably because a certain font isn't installed. Does Doom3 Demo come with any fonts? Maybe you could google how to install those fonts. Read the help files if the Doom3 people supplied them.

About the authentication error: You probably need to install some sort of protocol such as TLS or SSL or something like that. Again, read the help files if the Doom3 people supplied any.

I hope that helped a little.[/QUOTE]


killall esd worked thanks.
as for the font, don't know. doom3 doesn't mention anything.
will try TSL or SSL.

thanks,
a

---

### Post by aljones15 on 2005-09-30
btw is there anyway to just turn off esd so sound works all the time?

peace,
a

---

### Post by geekchic9 on 2005-09-30
If I remember correctly, go to system > preferences > sound and uncheck "enable sound server startup". I think that will turn off esd for GNOME but your sound will work for everything else. It's a somewhat confusing and frustrating workaround. This problem is supposed to be fixed in Breezy -- at least, I haven't had any problems with getting sound to work.

---

### Post by aljones15 on 2005-09-30
[QUOTE=geekchic9]If I remember correctly, go to system > preferences > sound and uncheck "enable sound server startup". I think that will turn off esd for GNOME but your sound will work for everything else. It's a somewhat confusing and frustrating workaround. This problem is supposed to be fixed in Breezy -- at least, I haven't had any problems with getting sound to work.[/QUOTE]

that seems to have worked too.
awesome. now just need to get doom 3 working and quake 3 demo

peace,
a

---

