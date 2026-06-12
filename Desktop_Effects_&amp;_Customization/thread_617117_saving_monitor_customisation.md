---
title: "saving monitor customisation"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by Rumpty on 2007-11-19
Running Ubuntu Gutsy.

 I have to use some gamma correction in the NVIDIA X server settings box to get my LCD to give a vaguely neutral grey scale. Even though I've tried saving the "x server display configuration", my adjustments are not remembered when the computer is re-booted.

Is there a way to record the changes somewhere?

---

### Post by MNICY on 2007-11-19
try opening the nvida settings with
```
sudo nvida-settings
```
in terminal.
you should be able to click the 'Save to X Configuration File' button and not get an error.

---

### Post by Rumpty on 2007-11-19
> **MNICY said:**
> try opening the nvida settings with
```
sudo nvida-settings
```
in terminal.
you should be able to click the 'Save to X Configuration File' button and not get an error.

That's just what I did, and the saving action seemed to work, but my settings were not remembered and recalled on the next boot.

---

### Post by Rumpty on 2007-11-19
There is now a file <nvidia-settings.rc> in my home directory, that has all the config changes in it that I want, so how do I get that file actioned?

---

