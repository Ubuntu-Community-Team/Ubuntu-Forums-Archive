---
title: "[SOLVED] Reproduir DVD"
date: 2008-08-11
forum: Catalan Team
---

### Post by Daerun on 2008-08-11
Suposo que aquest és un tema recurrent, però en fi, he buscat tot el que es podia buscar, tots els códecs necessaris i alguns que no coneixia libxine1-ffmpeg, libdvdread3, libdvdcss2, libdvdcss2-dev, i alguns altres... També ho he provat amb tot de reproductors: VLC, Mplayer, Smplayer, Kaffeine.... El resultat és que el máxim que puc veure és el primer capítol d'un DVD d'una sèrie. Amb Kaffeine he arribat a poder navegar pel menú del DVD, cosa que no puc fer amb els altres (VLC, per exemple, quan intento obrir el DVD, sencillament es tanca).
Estic bastant desconcertat, la veritat.

---

### Post by CarlesOriol on 2008-08-11
Doncs no, no crec que sigui un tema recurrent. De fet crec que és ja història.

Però bé... mirem que et succeeix.

Has probat amb el xine?

Pots mostrar-nos l'error que et dona per exemple fer mplayer dvd://1 o el totem desde linia de comandes o el vlc.

---

### Post by jmaspons on 2008-08-11
Hola,

a la wiki d'ubuntu ho expliquen:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

Cal afegir el repositori [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") i instal·lar el paquet libdvdcss2.

Espero que funcioni!

Salut

---

### Post by CarlesOriol on 2008-08-11
jmaspons: En Daerun diu que ja té insta&#320;lat el libdvdcss2 al seu missatge.

---

### Post by jmaspons on 2008-08-12
Tens raó. Pensava que potser hi ha diferents versions als repositoris oficials i als de Medibuntu, però si no és això ja no puc ajudar gaire més.

Salut!

---

### Post by Daerun on 2008-08-12
Efectivament, ja tenia el libdvdcss2.

El Xine no el tenia instal·lat, però vaig arribar a un enllaç en anglès (concretamente [AQUEST]("http://ubuntuguide.org/wiki/Ubuntu:Hardy") , a l'apartat REVISION ) on es parla d'aquest problema, i que dona com a possible solució les següents línies al terminal:

> sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list


sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update


sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs
En aquest últim vaig obviar la libdvdcss2. I noi, el xine va com la seda per als DVD :D

Vaig fer el que em dius (el *mplayer dvd://1* ), però ara no estic segur si ho vaig fer abans o després de tor el procés que he descrit :confused: (de vegades no sé on tinc el cap). De totes maneres enganxo el qué em va sortir, per si de cas hi hagués alguna cosa:

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 14 titles on this DVD.
There are 6 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: es aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: ac3 (5.1) language: es aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: es
number of subtitles on disk: 1
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  7000.0 kbps (875.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12


i a continuació s'obria una finestra on es començava a repdoduïr el primer capítol del disc.

---

### Post by CarlesOriol on 2008-08-13
Vaja... que vas insta&#320;lar el libcss dels repositoris de medibuntu i després el xine.

L'mplayer també sembla que et funcionava be... jo l'uso força amb l'mencoder en dvds.

---

### Post by Daerun on 2008-08-14
Doncs fins ara feia servir VLC per a gairebé tot, perquè em reproduïa prácticament tot (incloent coses que on el Totem em fallava), però no sé perquè, últimament el trobo bastant inestable, El xine no l'havia fet córrer mai i he de dir que, com a mínim per als DVD, m'ha agradat força :D

---

