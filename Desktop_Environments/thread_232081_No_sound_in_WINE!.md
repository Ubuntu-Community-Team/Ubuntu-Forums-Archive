---
title: "No sound in WINE!"
date: 2006-08-08
forum: Desktop Environments
---

### Post by seagull theme on 2006-08-08
When I run anything in wine :KS it has no sound.  When I go to winecfg and click the "audio" tab, I get this:

> shelley@shelley-desktop:~$ sudo winecfg
Password:
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
shelley@shelley-desktop:

---

### Post by kaffelars on 2006-08-08
This is, as far as I know, a common error, and there is a thread about it somewhere in the forum :)

---

### Post by RedKrieg on 2006-08-08
Try renaming ~/.asoundrc to ~/.asoundrc.backup
That worked for me.

Also, you shouldn't need to use sudo for winecfg...  the config options should be per user.

---

