---
title: "Totem Sound Gone after Kernel Panic..."
date: 2009-05-01
forum: General Help
---

### Post by AlphaMack on 2009-05-01
For some reason after a kernel panic forced me to reboot I have lost all audio in Totem whereas I get audio in other programs including mplayer, VLC, etc.  Opening the Pulseaudio volume control shows that there is indeed sound in Totem but nothing is coming out.

I tried Totem in other accounts on my machine and I DO get sound, so it's something specific to my account; perhaps a bad config file somewhere.

Any idea where to start looking?

---

### Post by AlphaMack on 2009-05-03
Never mind.

For some reason the selected output device was the microphone (in PulseAudio Device Chooser's Volume Control - Playback tab).  Switched it back to the correct device and I got sound again.

Strange.

---

