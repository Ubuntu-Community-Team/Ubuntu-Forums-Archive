---
title: "how to tell what mp3 codec is used"
date: 2005-11-16
forum: Desktop Environments
---

### Post by stoeptegel on 2005-11-16
Is there a way to see what codec is used to make a mp3 file?

---

### Post by mlomker on 2005-11-17
The **file** command-line tool?

```

mlomker@mlomkernote:~$ file Maroon\ 5\ -\ 01\ -\ Harder\ to\ Breathe.mp3
Maroon 5 - 01 - Harder to Breathe.mp3: MPEG ADTS, layer III, v1, 128 kBits, 44.1 kHz, JntStereo

```

---

### Post by stoeptegel on 2005-11-18
Nope it doesn't tell me when Lame, Xing or Blade is used as a mp3 encoder.

---

### Post by mlomker on 2005-11-18
[QUOTE=stoeptegel]Nope it doesn't tell me when Lame, Xing or Blade is used as a mp3 encoder.[/QUOTE]

Ah, I see.  That information isn't a part of the ID3 tag, so I'm not sure how a program would figure that out.

---

