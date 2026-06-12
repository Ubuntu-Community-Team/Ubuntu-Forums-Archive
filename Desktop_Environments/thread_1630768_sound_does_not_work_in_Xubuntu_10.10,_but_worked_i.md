---
title: "sound does not work in Xubuntu 10.10, but worked in Ubuntu 10.10"
date: 2010-11-25
forum: Desktop Environments
---

### Post by hekt0r on 2010-11-25
xfce mixer identifies my card (atiixp)  and i put the volume to the max and make sure there is no mute, but now sound comes out from flash nor mp3's, nor assualt cube. they all worked in ubuntu with gnome. any ideas?

---

### Post by alzaf on 2010-12-05
The following fixed the issue I had with no sound on Xubuntu 10.10

[LIST=1]
[*] Add the Mixer (volume control) to your menu panel (if you haven't got it on already)
[*] Click on Mixer
[*] In Sound card drop down menu select: **Playback: Internal Audio Analog Stereo (PulseAudio Mixer)**
[*] Click on Select Controls (The Select control dialog appears.)
[*] Click on Master. This will be now be ticked.  
[*] Press Close button
[*] Unmute the Master Control
[/LIST]

---

### Post by Mhoram on 2010-12-07
Thanks very much, Alzaf.  I lost sound on my laptop after doing an update last night, and your answer led me right to the problem:  the master control in that "Playback" controller was muted.

---

### Post by Skara Brae on 2011-01-01
[bump]

> **alzaf said:**
> The following fixed the issue I had with no sound on Xubuntu 10.10

[LIST=1]
[*] Add the Mixer (volume control) to your menu panel (if you haven't got it on already)
[*] Click on Mixer
[*] In Sound card drop down menu select: **Playback: Internal Audio Analog Stereo (PulseAudio Mixer)**
[*] Click on Select Controls (The Select control dialog appears.)
[*] Click on Master. This will be now be ticked.  
[*] Press Close button
[*] Unmute the Master Control
[/LIST]

After upgrading Xubuntu 8.04 to 10.04 two days ago, I discovered that I, too, had no sound.

Following the above brought the sound back :)

---

