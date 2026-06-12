---
title: "Sound is very low with totem"
date: 2005-11-02
forum: Desktop Environments
---

### Post by JeffBlouin on 2005-11-02
Hi,

        When I use Totem to watch a movie (avi dvd or Divx)  the sound is very low even when its on maximun setting.  

When I play the same file on Mplayer the sound is very good. The problem I have with Mplayer is that the Video image is very small in fullscreen... Any way to fix that?

Thanks!

---

### Post by mustang on 2005-11-02
[QUOTE=JeffBlouin]Hi,

        When I use Totem to watch a movie (avi dvd or Divx)  the sound is very low even when its on maximun setting.  

When I play the same file on Mplayer the sound is very good. The problem I have with Mplayer is that the Video image is very small in fullscreen... Any way to fix that?

Thanks![/QUOTE]

For the first problem, assuming you're using alsa, open up alsamixer 

```
alsamixer
```

and play around with the settings there. 

For the second problem, 

```
gmplayer -zoom <videofile>
```

---

### Post by JeffBlouin on 2005-11-04
Thanks...

Everything is now working A+

I was using ESD for sound... dont know why!

Jeff

---

