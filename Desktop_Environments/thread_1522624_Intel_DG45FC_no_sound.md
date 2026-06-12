---
title: "Intel DG45FC no sound"
date: 2010-07-02
forum: Desktop Environments
---

### Post by informel on 2010-07-02
I just did a clean install of Ubuntu 10.04 and the whole installation went fine.
 
My only problem is that I have no sound
MB is Intel DG45FC.
 
I know the hardware is OK because I tried it in Windows (dual booting).

---

### Post by 3Miro on 2010-07-02
What are you using default Ubuntu or something like Kubuntu (the latter is known to have some sound issues).

How do you test the sound? mp3/ogg or an YouTube video. You can go to Apps -> Accessories -> Terminal and type:
```
alsamixer
```
for YouTube, make sure that PCM is not lowered or muted. Check the other options as well.

If this doesn't help, you can try (again in the terminal)
```
sudo alsa force-reload
```

---

