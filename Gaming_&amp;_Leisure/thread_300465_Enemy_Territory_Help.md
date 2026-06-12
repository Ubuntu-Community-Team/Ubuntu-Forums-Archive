---
title: "Enemy Territory Help"
date: 2006-11-15
forum: Gaming &amp; Leisure
---

### Post by pissedoffdude on 2006-11-15
I just installed enemy territory but when i played it there was no audio. Does anybody know what I can do?

---

### Post by fatsheep on 2006-11-15
Try running these commands before running:

**NOTE: Remember to replace user:user with your own username! For me this is fatsheep:fatsheep.**

> sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 

Or you can make a startup script (just a text file with executable permissions):

> #!/bin/bash
sudo killall esd
chown user:user /proc/asound/card0/pcm0p/oss
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et 

When you run the script, it automatically automatically starts Enemy Territory with sound.

---

