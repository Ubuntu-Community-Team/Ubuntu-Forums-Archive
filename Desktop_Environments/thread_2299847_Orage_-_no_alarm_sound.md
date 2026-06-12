---
title: "Orage - no alarm sound"
date: 2015-10-21
forum: Desktop Environments
---

### Post by makem2 on 2015-10-21
Since upgrading to XFCE 4.12 Orage alarm sound has ceased to work.

I can check it within Orage using the 'Execute' button and see the reminder pop up but without sound.

The chosen sound and all other sounds play correctly and alarm sounds from Thunderbird work correctly. VLC plays all sounds.

The link between Orage and the sound file appear broken but the path shown is correct.

/home/makem/Music/SndFiles/sniffinglue.wav

Packages are up-to-date

Any suggestions please?

---

### Post by makem2 on 2015-10-21
Answer:

Orage defaultis to use 'play'. This was not installed by default.

sudo apt-get install sox

Better still, use the already manually installed VLC program editing Orage config file::

sudo nano ~/.config/orage/oragerc

Change:

Sound application=play [path to sound file]

to

Sound application=vlc [path to sound file]

ctrl x, save file

---

