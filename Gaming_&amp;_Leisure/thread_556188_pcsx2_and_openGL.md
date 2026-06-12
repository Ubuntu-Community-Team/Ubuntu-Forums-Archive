---
title: "pcsx2 and openGL"
date: 2007-09-21
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-09-21
Is there a way to run this emulator with a different plugin than openGL? I have intel gfx and it says "problem loading gs plugin"

---

### Post by process91 on 2007-10-06
I'm pretty sure that error is always in relation to the cg toolkit. Just install the cg toolkit and see what happens.

In feisty and below you'll need to download the RPM for your architecture [here]("http://developer.nvidia.com/object/cg_toolkit.html"), then use alien to convert it to deb and install it using dpkg.

In gutsy you can install it from the multiverse repo.

```
sudo apt-get install nvidia-cg-toolkit
```

I know you don't have nvidia, but try it out.

---

### Post by Ripfox on 2007-10-08
Nah. Same error...thnx for the try though. :)

---

