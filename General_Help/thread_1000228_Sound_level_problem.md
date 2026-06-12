---
title: "Sound level problem"
date: 2008-12-02
forum: General Help
---

### Post by rmcellig on 2008-12-02
I am running 8.10. I just hooked up a brand new pair of speakers. They seem to work but the sound level is rather low. I have the volume on the speakers set up all the way. The sound icon in the panel is also set up all the way. Is there another way to get the sound levels higher?

---

### Post by surfsunadam on 2008-12-02
Type 

alsamixer

into the terminal

Make sure all the bars are cranked.

---

### Post by rmcellig on 2008-12-02
The sound levels Master are at 100%. Any other ideas? I still have the volume all the way up on the speakers. Could it be an audio driver issue?

---

### Post by rmcellig on 2008-12-02
The master levels are at 100% The sound is up all the way on the speakers but the sound levels still aren't very high. Any other ideas? A sound driver issue?

---

### Post by Zorael on 2008-12-02
> **rmcellig said:**
> I just hooked up a brand new pair of speakers.
[list][*]Is the volume still low if you connect other speakers, earphones or headphones (if available)? *(to test for device malfunction)*
[*]Is it likewise low if you reboot onto a live cd/pendrive? Perhaps even an older version, like Hardy? *(to test for driver bugs)*[/list]

---

### Post by __Ryan__ on 2008-12-02
Check that the PCM is also cranked up in ALSA mixer. 

Alternatively you can right click on the sound icon and open volume control.  There is a graphical mixer there.

---

### Post by surfsunadam on 2008-12-02
Make sure you are plugged into the green output or headphone output on your sound card .. and yeah try some other headphones, speakers.

---

### Post by rmcellig on 2008-12-02
When I right clicked on the sound icon in the panel I noticed that the Master front levels were down. Turing them up did the trick.

Many thanks for all of your suggestions!!!! Really appreciate it.

---

