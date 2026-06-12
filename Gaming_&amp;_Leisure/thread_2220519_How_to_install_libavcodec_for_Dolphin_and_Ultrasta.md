---
title: "How to install libavcodec for Dolphin and Ultrastar?"
date: 2014-04-28
forum: Gaming &amp; Leisure
---

### Post by SSNova on 2014-04-28
I´m running Ubuntu 14.04 and i want to install Dolphin emulator and Ultrastar (a karaoke game). For dolphin I add the ppa but it didn´t work, then I downloaded the deb package from the dolphin website and when trying to install it requires the libavcodec53. And for ultrastar requires libavcodec52. 
 I´ve installed the libavcodec54 available for Trusty but it´s not solving the problem.

---

### Post by oldrocker99 on 2014-04-28
Well, there's this:
[http://packages.ubuntu.com/lucid/libavcodec52](http://packages.ubuntu.com/lucid/libavcodec52)

---

### Post by SSNova on 2014-04-28
Thanks, but wouldn´t have conflicts to have installed the 52 and 53 version?

---

### Post by oldrocker99 on 2014-04-28
It **shouldn't**, but I cannot say for sure. Worth a try, though.

---

### Post by SSNova on 2014-04-29
Ok, I´ll try it tonight an update how it went.

---

### Post by dannyboy79 on 2014-04-29
if it does cause conflicts you may have to compile from source by modifying the source code to look at the new libav version

---

### Post by sveni_lee on 2014-06-17
I tried to install UltraStar deluxe for Karaoke on my Ubuntu 14.04 HTPC.
The installation was okay but when try to start the Game via Advance Launcher 
the system freez. I checked the Error-log of UltraStar deluxe and found the following
massage:

```
UltraStar Deluxe V 1.1.0 Build Error Log
Date: 14-6-14 Time: 00:34:18
-------------------
ERROR:  libavformat header (54.20.4) and DLL (54.20.3) versions do not match.
ERROR:  Initialize failed, Removing - SDL_Playback
```

when I tried to start via console I received the following errors:

```
xbmc@mediacenter:/usr/games$ ./ultrastardx
An unhandled exception occurred at $000000000044822E :
EAccessViolation : Access violation
  $000000000044822E
  $00000000004D71DC
  $00000000004C9EA6
  $000000000047250B

xbmc@mediacenter:/usr/games$ sudo ./ultrastardx
Home directory not accessible: Keine Berechtigung
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_dsnoop.c:618:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
Cannot connect to server request channel
jack server is not running or cannot be started
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
Expression 'stream->playback.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 4611
SDL_SetVideoMode Failed [Initialize3D]
```

so i think I have done something wrong... 
Can anybody help? otherwise I have to start from the scretch with ubuntu 14.04.

---

