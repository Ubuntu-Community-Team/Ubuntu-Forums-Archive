---
title: "Sim City 3000 &amp; Ubuntu 11.04"
date: 2011-05-22
forum: Gaming &amp; Leisure
---

### Post by hambone79 on 2011-05-22
Ok, I have the old Loki Sim City 3000 game installed on my computer and everything was working perfectly until I upgraded to 11.04. Here is a run down of what I had to do to get it running:

I have a directory on my computer called /usr/local/games/SC3U/compat_libs which contains the following files:
```

ld-2.2.5.so
ld-linux.so.2
libanl-2.2.5.so
libanl.so.1
libasound.so
libasound.so.2
libasound.so.2.0.0
libBrokenLocale-2.2.5.so
libBrokenLocale.so.1
libc-2.2.5.so
libcrypt-2.2.5.so
libcrypt.so.1
libc.so.6
libdb1-2.2.5.so
libdb1.so.2
libdb.so.2
libdl-2.2.5.so
libdl.so.2
libfreetype.so
libfreetype.so.6
libfreetype.so.6.3.8
libGL.so
libGL.so.1
libGL.so.1.2
libm-2.2.5.so
libm.so.6
libnsl-2.2.5.so
libnsl.so.1
libnss_compat-2.2.5.so
libnss_compat.so.2
libnss_dns-2.2.5.so
libnss_dns.so.2
libnss_files-2.2.5.so
libnss_files.so.2
libnss_hesiod-2.2.5.so
libnss_hesiod.so.2
libnss_nis-2.2.5.so
libnss_nisplus-2.2.5.so
libnss_nisplus.so.2
libnss_nis.so.2
libopenal-0.0.so
libpthread-0.9.so
libpthread.so.0
libresolv-2.2.5.so
libresolv.so.2
librt-2.2.5.so
librt.so.1
libSDL-1.1.so.0
libSDL-1.2.so.0
libSDL-1.2.so.0.11.2
libSDL_mixer-1.0.so.0
libSDL_mixer-1.2.so.0
libSDL_mixer-1.2.so.0.2.5
libSDL_mixer.so
libSDL.so
libSDL_ttf-2.0.so.0
libSDL_ttf-2.0.so.0.6.2
libSDL_ttf.so
libSegFault.so
libsmjpeg-0.2.so.0
libsmjpeg-0.2.so.0.0.1
libsmjpeg.so
libsmpeg-0.4.so.0
libsmpeg-0.4.so.0.1.3
libsmpeg.so
libstdc++-3-libc6.2-2-2.10.0.so
libstdc++-libc6.2-2.so.3
libthread_db-1.0.so
libthread_db.so.1
libttf.so
libttf.so.2
libttf.so.2.2.0
libutil-2.2.5.so
libutil.so.1
libX11.so
libX11.so.6
libX11.so.6.2
libXcursor.so
libXcursor.so.1
libXcursor.so.1.0.2
libXext.so
libXext.so.6
libXext.so.6.4
libXfixes.so
libXfixes.so.3
libXfixes.so.3.0
libXrandr.so
libXrandr.so.2
libXrandr.so.2.0
libXrender.so
libXrender.so.1
libXrender.so.1.2.2
libz.so
libz.so.1
libz.so.1.1.4

```

I then use the following shell script to load the old libraries and get the game up and running:

```

#!/bin/bash
cd /usr/local/games/SC3U
LD_LIBRARY_PATH=/usr/local/games/SC3U/compat_libs/ SDL_AUDIODRIVER="dsp" SDL_PATH_DSP="/dev/dsp" /usr/local/games/SC3U/compat_libs/ld-linux.so.2 /usr/local/games/SC3U/sc3u.dynamic

```

Everything is working perfectly except for one small detail...no sound. When I run the script I get an error that it can't find /dev/dsp. Because of this I have tried using some of the OSS compatibility programs to get it to play nice, but nothing is working. So far I have tried aoss and padsp but neither will get the sound working.

Is there a way to create a actual /dev/dsp device that points to PulseAudio so I can get this up and running again?

BTW...I have tried installing oss-compat but the package appears to be broken as it does not know where to find the modules to load.

---

### Post by danbishop on 2011-05-24
I'm sure I read somewhere that OSS compatibility is completely broken with 11.04 and I don't think there are any plans to fix it... :(

---

