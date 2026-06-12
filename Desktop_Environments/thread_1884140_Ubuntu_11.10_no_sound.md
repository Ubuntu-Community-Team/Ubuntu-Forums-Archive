---
title: "Ubuntu 11.10 no sound"
date: 2011-11-20
forum: Desktop Environments
---

### Post by ptemple on 2011-11-20
Fresh install of 11.10, and I get no sound. From previous threads I have:

* ensured nothing is muted
* analogue output is selected
* reinstalling pulseaudio -
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo apt-get install ubuntu-desktop
sudo apt-get install sound-indicator
reboot
* tried changing sound permissions:
chmod -R a+rwX /dev/snd/*
* upgraded ALSA and rebooted:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
* installing kubuntu-desktop and trying sound from there

Nothing. Sound works perfectly in Microsoft Windows. Any ideas?

Phillip.

---

### Post by Drakul on 2012-01-18
If your motherboard has an onboard Intel HDA audio (ALC887), then follow these instructions:

1. Open the Terminal and run this command:

sudo gedit /etc/modprobe.d/alsa-base.conf

2. At the end of the file, add this line:

options snd-hda-intel model=generic

Save the file and reboot your system.

---

