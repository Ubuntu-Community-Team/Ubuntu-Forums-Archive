---
title: "Static Sound Fixable but How?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by BadServo on 2005-12-19
For some reason, anytime a sound plays in Ubuntu, I get dreadful background static.  I've tried several interesting things in various threads, and read through Intangeble's lengthy thread about ESD through ALSA.

Thus far nothing helps.  I finally discovered that if I play a sound file in XMMS and change the Output Plugin to ALSA, then click the "Configure" button below that option, and change "Audio Device" from "hw:0,0" to "hw:0,1" then sound plays perfectly in XMMS.

Thus far, I've been unable to find a meathod of making this a system-wide change.  As I'm sure is already apparent, I'm not the most knowledgable user when it comes to Linux, so if anyone can lend a hand or has a suggestion, it's much appreciated.

---

### Post by audax321 on 2005-12-19
I had a similar problem and ran alsamixer. Then I turned the volume up to max, but slowly turned the PCM volume down until the sound evened out. With the PCM volume turned all the way up I get horrible sound and bass that is very rough.

---

