---
title: "PCSX odd issue"
date: 2008-12-10
forum: Gaming &amp; Leisure
---

### Post by maddog46113 on 2008-12-10
In order to play PS games I have to use P.E.Op.SS Soft video plugin. Ive been playing final fantasy VIII but its annoying. The game runs slow without frameskip it doesnt seem to skip any frames when frameskip is on, however with frameskip on my final fantasy HUD in battle goes poof. The only way i can fight a battle is to turn off frameskip which causes the game to run about 3/4 speed. Ive tried other video plugins all of them lag. Any ideas on whats causing it?

(Only happens with the final fantasy series)
Chrono cross works 100% no missing frames 
Legend of Dragoon works 100% no missng frames.

PS: Opengl plugins crash the emulator.

---

### Post by hessiess on 2008-12-10
Have you tryed using pSX?

---

### Post by maddog46113 on 2008-12-10
> **hessiess said:**
> Have you tryed using pSX?

Yeah same result. Its something to do with the video plugin im using.

---

### Post by hikaricore on 2008-12-10
From the looks of your screenshots...  you should be disabling desktop effects when playing games.
That's really gonna kill your framerates unless you have top of the line video hardware.

---

### Post by dfreer on 2008-12-11
> **maddog46113 said:**
> Yeah same result. Its something to do with the video plugin im using.

That's odd, because pSX doesn't use video plugins the way ePSXe or PCSX do.

---

### Post by maddog46113 on 2008-12-11
> **dfreer said:**
> That's odd, because pSX doesn't use video plugins the way ePSXe or PCSX do.

I dunno ive tried so many including some for windows through wine. psx may have been the one that simply crashed everytime i tried to launch a game. I stuck with the one that works the best. I do disable desktop effects while playing. Nevertheless when i use the plugin im forced to use FF8 loses in battle frames. When i try using an opengl plugin all emulators give me the same response a big fat crash.

---

### Post by maddog46113 on 2008-12-11
> **dfreer said:**
> That's odd, because pSX doesn't use video plugins the way ePSXe or PCSX do.

I dunno ive tried so many including some for windows through wine. psx may have been the one that simply crashed everytime i tried to launch it. I stuck with the one that works the best. I do disable desktop effects while playing. Nevertheless when i use the plugin im forced to use FF8 loses in battle frames.

---

### Post by maddog46113 on 2008-12-11
Confirmed PSX crashes on lauch.

---

### Post by dfreer on 2008-12-11
> **maddog46113 said:**
> Confirmed PSX crashes on lauch.

Are you launching it from the terminal, what error is it giving you? I'm guessing it's the commonly reported issue with pulseaudio, which just requires a stop/kill of pulseaudio in order for pSX to work.

---

### Post by maddog46113 on 2008-12-11
> **dfreer said:**
> Are you launching it from the terminal, what error is it giving you? I'm guessing it's the commonly reported issue with pulseaudio, which just requires a stop/kill of pulseaudio in order for pSX to work.
 ```

aaron@Demonic:~$ '/home/aaron/Desktop/pSX/pSX' 

(pSX:1400): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:1400): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:1400): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:1400): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:1400): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:1400): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:1400): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:1400): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

Figured it was an opengl thing. I use a radeon 9200 proprietary drivers are not supported for this card in linux so im using the drivers that came with ubuntu.

---

### Post by Arylon on 2008-12-12
Final Fantasy VIII and a few other require frame skip turned off. This is a problem with the games themselves, not the plug-in or emulator.

The free drivers included with Ubuntu don't support OpenGL, so pSX and Open GL based plug-ins won't work.

As to what setting to use, it depends on what hardware you have, what version of the plug-in you have, are you using the included HLE Bios or one dumped from a real Playstation, and there are so many game-specific fixes to consider too.

The first thing is to make sure you are using the latest version of your plug-ins. P.E.Op.S. Linux Soft X GPU Version 1.18; Eternal SPU  v1.41 or P.E.O.P.s Linux OSS SPU  v1.8 are probably the most important ones to keep up-to-date. Also, try things with the default settings, low resolution, and check the fixes appropriate for games by Squaresoft and Final Fantasy in particular.

pSX is really the easiest way to get things running, but it requires OpenGL and therefore the restricted drivers. I don't suppose there's any way you could upgrade your graphics card?

---

