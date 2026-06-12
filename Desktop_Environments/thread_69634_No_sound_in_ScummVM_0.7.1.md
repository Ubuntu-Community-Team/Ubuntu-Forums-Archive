---
title: "No sound in ScummVM 0.7.1"
date: 2005-09-27
forum: Desktop Environments
---

### Post by Jackster on 2005-09-27
Hey guys, I've been trying to run ScummVM recently, but it has no sound. At first I thougt it may have been due to the old version i was running (0.6.1), so I went and downloaded the .deb from the site and installed 0.7.1, but still no sound. I went into the sound options part and chose ALSA, since that's what im using (i think), but still no joy. 

Anyone have any suggestions?

Thanks
Jack

EDIT: and this is the only program on my system that wont play sound

---

### Post by compless on 2005-10-27
[QUOTE=Jackster]Hey guys, I've been trying to run ScummVM recently, but it has no sound. At first I thougt it may have been due to the old version i was running (0.6.1), so I went and downloaded the .deb from the site and installed 0.7.1, but still no sound. I went into the sound options part and chose ALSA, since that's what im using (i think), but still no joy. 

Anyone have any suggestions?

Thanks
Jack

EDIT: and this is the only program on my system that wont play sound[/QUOTE]

Sorry for bumping a 4 weeks old thread but I had this problem also.
I solved it by installing the libsdl alsa package from repository.

---

### Post by GonZo on 2006-01-31
ok, it works for me and i can hear the voices but music still doesn't work

---

### Post by LordBug on 2006-02-28
If you already solved this, then ignore.  I finally managed to get sound and music working in SCUMMVM.  It took some digging to get the info.

This all assumes you have SCUMMVM installed from Synaptic (currently 0.7.1).

1) Pop into Synaptic and install libsdl-alsa.  This will delete libsdl-oss.  I don't want OSS, so I don't care.  This will allow you to use "ALSA" in ScummVM.

2) Midi music.  This is a tricky one.  You'll need to read:
[This one for software MIDI synthesis](https://wiki.ubuntu.com/MidiSoftwareSynthesisHowTo)
[This one for hardware MIDI synthesis](http://ubuntuforums.org/showthread.php?t=30963)

3) Set ScummVM audio to "Default".

Following these (hardware MIDI for me) got me sound effects and full music in Beneath a Steel Sky.  I have yet to try with other games.

---

