---
title: "How to get hardware decoding working in steam"
date: 2016-01-18
forum: Gaming &amp; Leisure
---

### Post by FlakeyBanana on 2016-01-18
So for about 3 days now ive been attempting to get hardware decoding to work. With windows 10 installed it works, but with Ubuntu 15.10 and steam the in game overlay shows 4 thread software decoding and the log says


```

Fri Jan 15 21:39:14 2016 UTC - CVAAPIAccel: Couldn't load libva-x11.so.1
Fri Jan 15 21:39:14 2016 UTC - VDPAU init failed: GL_NV_vdpau_interop not available on current context
Fri Jan 15 21:39:14 2016 UTC - libavcodec software decoding with 4 threads



```

Vainfo result

```
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_33
libva info: va_openDriver() returns 0 
vainfo: VA-API version: 0.38 (libva 1.6.0)
vainfo: Driver version: AMD MMD 1.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileMPEG4Simple            : VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    : VAEntrypointVLD
      VAProfileMPEG4Main              : VAEntrypointVLD
      VAProfileH264Baseline           : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Simple              : VAEntrypointVLD
      VAProfileVC1Main                : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```
Thanks for any help (:


AMD 6600M with the latest version of the drivers compiled and installed from the AMD website

---

