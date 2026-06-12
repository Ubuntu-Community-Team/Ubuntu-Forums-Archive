---
title: "cedega, warcraft3, amd64, dri?"
date: 2005-05-11
forum: Gaming &amp; Leisure
---

### Post by crazedcougar on 2005-05-11
Hi,

I just installed cedega on my amd64 machine yesterday, and have found it very easy to install and setup.  Sound works, i have a nice resolution, and dri says it works.  I have the radeon9600SE, here is some output:

fglrxglxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

```

glxgears runs jerkily, and delivers a low fps:
```
3267 frames in 5.0 seconds = 653.400 FPS
3673 frames in 5.0 seconds = 734.600 FPS
3671 frames in 5.0 seconds = 734.200 FPS
```

fgl_glxgears runs good, gives an even lower fps:
```
720 frames in 5.0 seconds = 144.000 FPS
733 frames in 5.0 seconds = 146.600 FPS
748 frames in 5.0 seconds = 149.600 FPS
```

Is this normal?  I have tried starting warcraft with cedega, it gets less than one fps.  I had a similar [problem on gentoo](http://forums.gentoo.org/viewtopic-t-323535-highlight-.html) , could they be related?  If not, what is the cause?

BTW, in order to get sound in warcraft, you need to killall esd, is there a way to avoid this?

Thanks,
--Peter

---

### Post by gil-galad on 2005-05-11
[QUOTE=crazedcougar]
BTW, in order to get sound in warcraft, you need to killall esd, is there a way to avoid this?

Thanks,
--Peter[/QUOTE]

That probably means that your sound card doesn't support hardware mixing in linux, meaning you can only listen to one program at a time.  Esd provides software mixing, but as far as I know cedega can't use it.  What sound card do you have?

If your running the amd64 version of ubuntu, the problem you had with gentoo is probably related.  I wish I could help you, but I am still stuck with a 32-bit processor myself  :neutral:

---

### Post by crazedcougar on 2005-05-12
i've modified my esd conf like on ubuntuguide, i can listen to music and gaim sounds and neverball sounds at once.  There seems to be another older thread about [this](http://ubuntuforums.org/showthread.php?t=28281&highlight=sound+warcraft) , i have not tried it yet.

Any 64 bit guru know where to set the driver paths to?

--Peter

---

