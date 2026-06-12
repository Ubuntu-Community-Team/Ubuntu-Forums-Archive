---
title: "New sound card"
date: 2008-12-24
forum: General Help
---

### Post by imtheguido on 2008-12-24
I am running ubuntu 8.10 intrepid and I have just recently installed a new sound card. For some reason, I cannot get any applications to run through that sound card. Everything is running on the onboard sound of the system. But the system volume control does not effect the volume in any way.

When I go into System->Preferences->Sound I am able to get sound to come out of my head phones when I have OSS - Open Sound System selected for the tests. It also works if I have C-Media Oxygen HD Audio (rev 2) analog (OSS) selected for all of the options, though it is not given for the bottom option of Default Mixer Tracks. When I have all of them set to OSS all of the tests work, but yet I still cannot get any sound to run from any applications. Some help please?

---

### Post by linux_tech on 2008-12-24
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first

```
sudo apt-get install gnome-alsamixer
```

To open gnome-alsamixer type

```
gnome-alsamixer
```

check all settings, make sure nothing is muted

To open volume control type:

```
gnome-volume-control
```

---

### Post by imtheguido on 2008-12-24
Alright, I installed that Mixer. And I am still getting no sound. In the volume control it gives me a bunch of options, none of which work...

The options are:
C-Media CMI8788 (Alsa Mixer)
Intel 82801DB-ICH4 (Alsa Mixer)
CMI8788 (OSS Mixer)
Playback: ALSA PCM on front:1 (Intel 82801DB-ICH4) via DMA (BulseAudio Mixer)
Playback: ALSA PCM on front:0 (analog) via DMA (PulseAudio Mixer)
Capture: Monitor Source of ALSA PCM on front:1 (Intel 82801DB0-ICH4) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on front:1 (Intel 82801DB-ICH4) via DMA (PulseAudio Mixer)
Capture: Monitor Source of ALSA PCM on Front:0 (Analog) via DMA (PulseAudio Mixer)
Capture: ALSA PCM on front:0 (Analog) via DMA (PulseAudio Mixer)

None of these match the earlier ones I could go in and test with the Sound Preferences.

---

### Post by linux_tech on 2008-12-24
next try restarting alsa

```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start

```

---

### Post by imtheguido on 2008-12-24
Alright, did that. Still no sound.

---

### Post by imtheguido on 2008-12-24
Bump

---

### Post by linux_tech on 2008-12-24
This will temporarily stop pulseaudio
In terminal type-
```
 killall pulseaudio
```
then try sound again

---

