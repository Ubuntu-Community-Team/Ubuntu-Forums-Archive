---
title: "ALSA dmix (software audio mixing) - Rough explanation"
date: 2005-11-16
forum: Desktop Environments
---

### Post by suoko on 2005-11-16
ALSA DMIX only works with applications which support ALSA or aoss. It doesn't work with applications which support OSS only.(It might not be a technically correct explanation but it gives you an idea)


Applications which support DMIX:

- rhythmbox
- totem
- vlc
- mplayer
- gaim
- xine
- xmms
- alsaplayer
- gnome-sound-recorder (if only this app ever worked...)
- realplayer (through aoss)
- avidemux (through aoss - bad sound)
- flash player in firefox (through aoss - modify /etc/mozilla-firefox/mozilla-firefoxrc to FIREFOX_DSP="aoss")


Applications which don't support DMIX:

- skype
- gizmo
- audacity
- java plugin
- flash player in epiphany

WHAT IS aoss?
aoss lets applications written for OSS use ALSA output, therefore it works with DMIX.

HOW TO USE aoss?
EXAMPLE: aoss realplay

---

