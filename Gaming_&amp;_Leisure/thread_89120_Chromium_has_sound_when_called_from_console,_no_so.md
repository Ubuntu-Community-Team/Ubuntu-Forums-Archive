---
title: "Chromium has sound when called from console, no sound when started from panel"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by agro1986 on 2005-11-11
Chromium sound works perfectly when run from console, but doesn't when run from the Applications menu (even when Terminal is set to true in chromium.desktop). Here are the relevant info:

Installing chromium:

```

sudo apt-get install chromium

```

The deb files used to install chromium:

```

chromium-data_0.9.12-2_all.deb
chromium_0.9.12-7ubuntu1_i386.deb

```

/usr/share/applications/chromium.desktop:

```

[Desktop Entry]
Encoding=UTF-8
Name=Chromium
Comment=Scrolling space shooter
Exec=chromium
Icon=chromium
Terminal=true
Type=Application
Categories=Application;Game;
StartupNotify=false

```

(I have tried Terminal true and false, and StartupNotify true and false)

Partial log when calling "chromium" from gnome-terminal:

```

...
GL_SGIS_generate_mipmap         GL_SGIS_multitexture
GL_SGIS_texture_lod             GL_SUN_slice_accum
------------------------------------------------------------
1 CDROM drive(s).
-OpenAL-----------------------------------------------------
Vendor     : J. Valenzuela
Renderer   : Software
Version    : 0.0.7
Extensions :
AL_EXT_capture                  AL_EXT_vorbis
AL_EXT_MP3                      AL_LOKI_quadriphonic
AL_LOKI_play_position           AL_LOKI_WAVE_format
AL_LOKI_IMA_ADPCM_format        AL_LOKI_buffer_data_callback
ALC_LOKI_audio_channel
------------------------------------------------------------
ATTENTION!! Could not load alAttenuationScale
alAttenuationScale == 0. Kludge it.
...startup complete.
...

```

Partial log when running Chromium from the Applications menu with Terminal set to on:

```

...
GL_SGIS_generate_mipmap         GL_SGIS_multitexture
GL_SGIS_texture_lod             GL_SUN_slice_accum
------------------------------------------------------------
1 CDROM drive(s).
open /dev/[sound/]dsp: Device or resource busy
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!! ATTENTION !! - one or more errors were encountered during audio check.
!!                Audio will be disabled.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
...startup complete.
...

```

Any idea?

---

### Post by agro1986 on 2005-11-11
Hmm... The problem also happens with tuxkart and clanbomber. tuxkart output from console:

```

Data files will be fetched from: '/usr/share/games/tuxkart'
Data files will be fetched from: '.'


   TUXEDO T. PENGUIN stars in TUXKART!
               by Steve and Oliver Baker
                 <sjbaker1@airmail.net>
                  http://tuxkart.sourceforge.net


Kart 0 == 'tuxkart.ac'
Kart 1 == 'geekokart.ac'
Kart 2 == 'bsodkart.ac'
Kart 3 == 'gownkart.ac'
READY TO RACE!!

```

tuxkart output from panel (no sound):

```

Data files will be fetched from: '/usr/share/games/tuxkart'
Data files will be fetched from: '.'


   TUXEDO T. PENGUIN stars in TUXKART!
               by Steve and Oliver Baker
                 <sjbaker1@airmail.net>
                  http://tuxkart.sourceforge.net


slDSP: open: Device or resource busy
WARNING: slScheduler: soundcard init failed.
Kart 0 == 'tuxkart.ac'
Kart 1 == 'geekokart.ac'
Kart 2 == 'bsodkart.ac'
Kart 3 == 'gownkart.ac'
READY TO RACE!!

```

Clanbomber gives no output to the console.

Btw, other games like TuxRacer, supertux, bumprace, and armagetron sounds fine when launched from the panel.

---

### Post by lateo on 2005-11-12
same as for Enemy-Territory and other stuff:
if u lanch it from the pannel u should disable sound event.
system>preferences>sound, events, user interface>'choose menu element' -> no sound at all.

hope this helps.

---

