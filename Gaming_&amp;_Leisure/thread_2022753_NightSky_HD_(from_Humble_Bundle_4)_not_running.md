---
title: "NightSky HD (from Humble Bundle 4) not running"
date: 2012-07-11
forum: Gaming &amp; Leisure
---

### Post by kiddykoff on 2012-07-11
I'm coming across a problem when trying to run NightSkyHD_64 on Ubuntu.

```
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Segmentation fault (core dumped)

```

I've already tried installing the jack package, but that hasn't helped.

---

### Post by thatguruguy on 2012-07-11
> **kiddykoff said:**
> I'm coming across a problem when trying to run NightSkyHD_64 on Ubuntu.

```
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Segmentation fault (core dumped)

```I've already tried installing the jack package, but that hasn't helped.

It's not because of Jack. I get the same errors, but NightSky runs fine on my system.

What kind of video system do you have? What happens when you run the regular NightSkyHD package, rather than NightSkyHD_64?

---

### Post by kiddykoff on 2012-07-12
When i run the regular package, i just get the segmentation fault and core dumped

As for my video,

ATI Mobility Radeon HD 4200 Series 256 MB

---

