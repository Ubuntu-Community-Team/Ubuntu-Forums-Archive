---
title: "audio problem: can't record"
date: 2005-04-17
forum: Desktop Environments
---

### Post by [censored] on 2005-04-17
None of my recording programs pick up anything. 

If I open the utility Gnome Menu->Sound & Video -> Volume Control,  go to the Capture Tab, and turn the mic volume up ...  I can hear sound I'm putting in the mic coming through the speakers. But none of the recording apps pick it up. 

For e.g, $rec test.wav just produces an empty wav file. Audacity, similar results. Same deal with tool in the Gnome Menu called Recorder. 

What do I need to tweak?

---

### Post by word_virus on 2005-04-17
If you can hear your mic audio through your speakers but it's not being recorded it means you've turned up the mic Playback channel and not the mic Record channel in the mixer.  Some more specific hardware info would be helpful, like what kind of sound card you have.  For instance, I have a SB Audigy 2 whose Mic channel is actually "Line 2" in the mixer.

---

### Post by [censored] on 2005-04-17
I have actually selected Mic as the record source in the Volume control. Here's a (300k) screenshot [http://haha.what.a.phunny.name/~pirch/Screenshot-1.png](http://haha.what.a.phunny.name/~pirch/Screenshot-1.png)

The soundcard is a Creative SB Live 5.1. The drivers appear to be snd_emu10k1.

---

