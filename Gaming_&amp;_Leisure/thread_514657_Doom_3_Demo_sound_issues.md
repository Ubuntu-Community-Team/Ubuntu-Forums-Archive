---
title: "Doom 3 Demo sound issues"
date: 2007-08-01
forum: Gaming &amp; Leisure
---

### Post by Zeikcied on 2007-08-01
I downloaded the Doom 3 demo (mainly to see if graphics comparable to Unreal Tournament 3 will run on my system).  The game works, but the sound doesn't.

Now, I get sound.  Getting the sound isn't the problem.  The problem is that the sound is all messed up.  It sounds a bit jumbled.  The music skips, and the voice overs are impossible to understand.

I've tried using Alsa and OSS, with the default device and plughw:0.  All options give the same result.  (I do have the alsa-oss package, and I had it before I installed the demo.)

Is there any way to fix it?

---

### Post by longfire on 2007-08-01
Try adding " +set s_driver oss +set s_numberOfSpeakers 2 "

For example when I put a shortcut in my applications folder I typed the folder and the code. That got my sound working so I didn't have to type it out in terminal each time

ie:

/usr/local/games/doom3-demo/doom.x86 +set s_driver oss +set s_numberOfSpeakers 2


This should work for Quake Demo also

---

### Post by Zeikcied on 2007-08-01
> **longfire said:**
> Try adding " +set s_driver oss +set s_numberOfSpeakers 2 "

For example when I put a shortcut in my applications folder I typed the folder and the code. That got my sound working so I didn't have to type it out in terminal each time

ie:

/usr/local/games/doom3-demo/doom.x86 +set s_driver oss +set s_numberOfSpeakers 2


This should work for Quake Demo also
I've set s_driver to "oss" in the config file, and the config file also has s_numberOfSpeakers set to 2.  I still had problems with those settings.  (I only have two speakers, and I turned off the Surround setting in the options menu.)

---

### Post by RabidWeezle on 2010-05-27
First Install Aoss then edit your config:
```

sudo apt-get install alsa-oss
gedit ~/.doom3/base/DoomConfig.cfg

```

edit the seta s_driver line to say:
```

seta s_driver "oss"

```
then save and close.

Start the game with:
```

aoss doom3

```

---

### Post by Cresho on 2010-05-27
i shot pulseaudio from the air and doom audio works fine.

---

