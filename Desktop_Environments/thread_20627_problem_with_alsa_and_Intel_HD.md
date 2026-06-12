---
title: "problem with alsa and Intel HD"
date: 2005-03-17
forum: Desktop Environments
---

### Post by Sivel on 2005-03-17
I decided to switch to Hoary Hedgehog from Fedora core 3 a few days ago and am very pleased except for the fact I cannot get alsa/sound card to work properly.

In fedora I downloaded the src for alsa 1.08 and did ./configure;make;make install and installed support for all sound cards.  Now I did the same thing with Ubuntu and my sound card is now recognized but any time I try and run a program that uses sound such as XMMS to play an mp3 I get the error message "Couldn't open audio: Please check that: Your sound card is configured properly, You have the correct output plugin selected, No other program is blocking the soundcard"

MPlayer just freezes and it won't do anything.  I have tried uninstalling alsa from the synaptic package manager but that just causes more problems because it uninstalls gnome.  I installed alsa then used apt-get install gdm and it overwrote the alsa that I just installed.

Any suggestions or ideas?

---

### Post by telmo on 2005-03-17
Yep! I have EXACTLY the same problem! And noone has been able to help me so far...    :cry:

---

### Post by alastair on 2005-03-17
I might not be able to help - but it seems to me that a latest Hoary install /should/ be setup (pretty much) for alsa/sound to work. I think a source download and install is a last resort really now - and an apt install much preferable (if you are missing things).

I have an intel "AC'97 Audio Controller" (lspci) and my sounds seems fine (thinkpad, xmms, mplayer etc.).

I have installed :

root@muse:/home/alastair # dpkg -l '*alsa*'|grep '^ii'
ii  alsa-base      1.0.8-4ubuntu2 ALSA driver configuration files
ii  alsa-oss       1.0.7-1        ALSA OSS-compatibility application wrapper
ii  alsa-utils     1.0.8-1ubuntu1 ALSA utilities
ii  alsaplayer     0.99.76-0.2ubu PCM player designed for ALSA
ii  alsaplayer-als 0.99.76-0.2ubu PCM player designed for ALSA (ALSA output mo
ii  alsaplayer-com 0.99.76-0.2ubu PCM player designed for ALSA (common files)
ii  alsaplayer-gtk 0.99.76-0.2ubu PCM player designed for ALSA (GTK version)
ii  alsaplayer-jac 0.99.76-0.2ubu PCM player designed for ALSA (jack output mo
ii  alsaplayer-oss 0.99.76-0.2ubu PCM player designed for ALSA (OSS output mod
ii  gstreamer0.8-a 0.8.8-0ubuntu1 ALSA plugin for GStreamer
ii  libpt-plugins- 1.8.4-1        Portable Windows Library Audio Plugin for th
ii  polypaudio-als 0.7-0ubuntu5   ALSA modules for the polypaudio sound server

If this is a NEW install (and you can afford this), I'd be tempted to install from scratch - the latest snapshot of Hoary and try again (see above packages perhaps) :

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/hoary/current/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/hoary/current/)

---

