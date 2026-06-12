---
title: "Volume Manager - No Sound -  Lubuntu 12.04 - Asus Laptop"
date: 2012-07-27
forum: Desktop Environments
---

### Post by anonranger on 2012-07-27
1. I installed Lubuntu 12.04 in my ASUS laptop. I got no sound.

I did the following as below to make it work.

[http://askubuntu.com/questions/80384/where-are-the-lxde-sound-preferences](http://askubuntu.com/questions/80384/where-are-the-lxde-sound-preferences)

"

to install

sudo apt-get install xfce4-mixer gstreamer0.10-alsa
This installs the following limited number of xfce packages -

exo-utils libgarcon-1-0 libgarcon-common libwnck-common libwnck22 libxres1
  xfce4-mixer xfce4-panel
to run

type xfce4-mixer in a lxterminal

[B]In Options Auto-Mute Mode

It should be set as Disabled.[/B]

"

2. We need a volume manager in Lubuntu.

This is a basic feature, is there a reason why this is not installed in Lubuntu.

---

