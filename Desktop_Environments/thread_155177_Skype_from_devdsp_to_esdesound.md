---
title: "Skype from /dev/dsp to esd/esound"
date: 2006-04-04
forum: Desktop Environments
---

### Post by Dutch on 2006-04-04
I used this HowTo for my sound:

```

http://www.ubuntuforums.org/showthread.php?t=101125

```

And it says that the sound has to be through esd/esound.

But Skype sound says /dev/dsp

I can't find a config file in Skype to change this.
Because when I use and Streamtuner and Skype it says there is a sound problem.

U got the answer ?

---

### Post by queenorych on 2006-04-05
esddsp skype

From man page "esddsp - attempt to reroute audio device to esd"

there is a problem with skype for linux not properly closing and reopening the audio device.  See skype_hijacker [http://195.38.3.142:6502/skype/](http://195.38.3.142:6502/skype/)

---

