---
title: "Brasero"
date: 2009-05-31
forum: General Help
---

### Post by RedSingularity on 2009-05-31
Why cant i rip audio cds with brasero?  It just shuts down when i try.  So i just took them from the CD and copied them to the desktop.  They are now .wav files.  When i try to copy these to a cd via brasero i get a message saying that the .wav files are empty, thus i cannot move them to a cd.  Any suggestions?

---

### Post by VMC on 2009-05-31
> **Shadow121 said:**
> Why cant i rip audio cds with brasero?  It just shuts down when i try.  So i just took them from the CD and copied them to the desktop.  They are now .wav files.  When i try to copy these to a cd via brasero i get a message saying that the .wav files are empty, thus i cannot move them to a cd.  Any suggestions?

What just shuts down, Brasero? If so run it from a terminal like so:

```
brasero --debug &>brasero-debug.txt
```

---

### Post by zero777zero on 2009-06-01
> **Shadow121 said:**
> So i just took them from the CD and copied them to the desktop.  They are now .wav files.

this doesnt work, CD-A stores raw PCM streams which need to be converted to WAV. i run ExactAudioCopy through Wine for a perfect rip. rubyripper is also supposed to be a good ripper for linux if you prefer native.

---

