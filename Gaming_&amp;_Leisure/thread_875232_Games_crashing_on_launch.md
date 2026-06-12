---
title: "Games crashing on launch"
date: 2008-07-30
forum: Gaming &amp; Leisure
---

### Post by jdenicholls on 2008-07-30
Ok recently I installed some new video drivers for my graphics card. They seem to have installed correctly, I can access all the relevant options through the utility that came with it for config. However a few games that previously work now crash. Steam is one of them, which I'm operating through Wine, but oddly enough Pingus is another one. When I try to launch it from the terminal here is what happens:

Welcome to Pingus 0.7.2!
========================
data path:               /usr/games/../share/games/pingus/data/
language:                English (en)
font encoding:           iso-8859-1
sound support:           enabled
music support:           enabled
resolution:              800x600
fullscreen:              disabled

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Unable to initialize SDL_Mixer: No available audio device
Pingus: Unknown throw caught!

Can anyone explain to me what the problem is and how to fix it?

---

### Post by Dark Aspect on 2008-07-30
The error Pingus gave seems to be related to the audio,did you try Pingus before the you installed the new video drivers? How did you install the graphics driver?

---

### Post by jdenicholls on 2008-07-31
Pingus **did** work before I installed the new video drivers. I installed them by working through the terminal using these commands:

> 
download the driver to your /home dir.
sudo apt-get install build-essential
ctrl+alt+f1
login
sudo chmod +x NV*
sudo /etc/init.d/gdm stop
sudo sh NV*
Follow onscreen directions
sudo /etc/init.d/gdm start
enjoy

I expect it's a problem with the sound, given the readout of the terminal.

---

### Post by CirtexHosting on 2008-07-31
Looks loke sound related issue. If it is possible can you modulate initial situation and check?

---

### Post by jdenicholls on 2008-07-31
I reinstalled the drivers and I can run Pingus again! However I've really got to test out the drivers on some proper games. I'm installing Team Fortress 2 at the moment and hopefully I can get it to run properly. I'll post back saying whether I've solved the problem.

---

