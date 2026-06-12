---
title: "Weird soundcard trouble"
date: 2007-06-17
forum: Dell  Ubuntu Support
---

### Post by tompouce on 2007-06-17
Hi!

That's weird, when I mute the sound, there's like only basses playing, and when I drop the PCM slider there's no more sound, it's like it's been splitted between master and PCM and there's another sound card called sigmatel and one called intel wtf?

Thanks a lot! i have an inspiron 9300

---

### Post by neptho on 2007-06-17
This means you are probably using both ALSA and the OSS emuation for your tools.

What are you using to controll your audio?  You can use alsamixer from the terminal.

The Sigmatel driver is the OSS version, the HD Intel is the ALSA device.  You can change which (virtual) device you are using by going to 'Applications', 'Sound and Video', 'Volume Control', then 'File', 'Change Device'.

OSS is antiquated and will eventually be removed, it's best to use the ALSA devices.  If an application is written to use OSS, you can usually coax it into using the ALSA driver by installing 'alsa-utils' and changing the launcher to call 'aoss <program name>'  (Right click menu, edit menu, find the program, double click, then change from 'program' to 'aoss program' AFTER installing alsa-utils).

---

