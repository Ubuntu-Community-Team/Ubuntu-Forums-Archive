---
title: "Bumpy replay of Quicktime movies"
date: 2005-12-07
forum: Desktop Environments
---

### Post by agger on 2005-12-07
Hi,

I have a digital camera capable of recording videos. 
These videos are stored in Apple Quicktime (.MOV) format.

When playing these videos in Linux (using xine or mplayer), 
the sound is always bumpy and jumpy and grainy, and the
video is shaky.

When playing them using Quicktime in Windows, they're fine!

I've got all the multimedia plugins installed. What am I doing
wrong?

TIA for any help.

---

### Post by agger on 2005-12-07
This question was also discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=90539&highlight=Quicktime+.mov](http://ubuntuforums.org/showthread.php?t=90539&highlight=Quicktime+.mov)

where some suggestions were made. I'm not at my Ubuntu box right now, but if I make this work, I'll let you know.

---

### Post by agger on 2005-12-07
This baby worked wonders!

[QUOTE=authortitle]use srate=48000 (it defaults to 44100) - I just added srate=48000 to my ~/.mplayer/config and it all seems fine :)
[/QUOTE]


I don't know what it means, but it sure works. :-)

---

### Post by Spacecaptain on 2005-12-21
srate seems to be the sampling rate for sound.
44100 Hz is kind of a standard in digital sound files, but it seems that that QT has decided to use 48000 instead.... one wonders why oh why?

---

