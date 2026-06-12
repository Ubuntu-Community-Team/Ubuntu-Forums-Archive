---
title: "Mini 9 Internal Mic"
date: 2008-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bd_thompson on 2008-10-17
OK, I'm stumped.  I've tried every combination in the sound manager and cannot get the internal mic to work.

Any suggestions?  Thanks.

---

### Post by bd_thompson on 2008-10-18
> **bd_thompson said:**
> OK, I'm stumped.  I've tried every combination in the sound manager and cannot get the internal mic to work.

Any suggestions?  Thanks.

Anyone?

---

### Post by Denny Johnson on 2008-10-18
i got mine working in my 1420n by double clicking the speaker icon > OPTIONS > Digtal Input Source: Digital Mic 1.

---

### Post by Denny Johnson on 2009-03-22
A friend is getting a mini 9, Dell is telling him that it does not have an internal mic if you do not get the webcam option. Is that true?
Thanks

---

### Post by bd_thompson on 2009-03-22
> **Denny Johnson said:**
> A friend is getting a mini 9, Dell is telling him that it does not have an internal mic if you do not get the webcam option. Is that true?
Thanks

Can't answer since mine came with both. 

Dave Thompson

---

### Post by jespdj on 2009-03-22
I have a Mini 9 (with webcam), and I'm using Ubuntu 8.10 on it.

First, I applied the fixes for 8.10 mentioned in [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support](http://ubuntuforums.org/showthread.php?t=789578).

To make the microphone work, I did this:
- Double click the volume icon in the top right of the screen
- Select Preferences; enable "Capture" and "Capture 1" and both "Input Source" options
- You'll now have a Recording and an Options tabsheet in the volume control.
- On the Options tabsheet, set the first Input Source to "Front Mic".
- On the Capture tabsheet, set the volume for "Capture" (this is the volume for the microphone).

Test using Sound Recorder (Applications / Sound & Video / Sound Recorder).

---

