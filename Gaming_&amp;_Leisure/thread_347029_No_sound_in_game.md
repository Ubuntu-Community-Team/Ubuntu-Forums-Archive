---
title: "No sound in game"
date: 2007-01-26
forum: Gaming &amp; Leisure
---

### Post by tater_3001 on 2007-01-26
i recently installed Oni on my computer and it has no sound... i was wondering if there is a way to fix this, the game just isn't as awesome without sound.. Thanks, Turner

---

### Post by jso2897 on 2007-05-08
Try this, if you feel like it - probably won't work: Uninstall oni, then CD up to the CDROM drive, put the disc in, and in terminal "wine autorun.exe"(or whatever the automatic start app on the cd in named)
Set up the game in the Windows shell, and then play it the same way - autorun the disc and select "play" from the menu.
It might be worth a try.:-k

---

### Post by mbradlcu on 2007-05-09
I'm not sure if this is relevant but quake2 based games have the same problem, it's due to the excutable not being able to use /dev/dsp,, here's the fix:
echo 'kingpin 0 0 direct' > /proc/asound/card0/pcm0p/oss
fuser -vk /dev/dsp

you'll need to run them sudo

---

### Post by donfilipo on 2007-05-11
> **mbradlcu said:**
> I'm not sure if this is relevant but quake2 based games have the same problem, it's due to the excutable not being able to use /dev/dsp,, here's the fix:
echo 'kingpin 0 0 direct' > /proc/asound/card0/pcm0p/oss
fuser -vk /dev/dsp

you'll need to run them sudo


Well i discovered lately that linux in fact has quite a few game choices. Until i was running Tux racer, you could not take linux serious for a gaming OS. Ok...but since i installed Kingpin: Life of a crime...i can not sleep. First installation with cedega...no go - only the multiplayer worked in case if i myself put up a server....single player ended with an error: "cannot use 'all' as the device name". Then i found a loki installer which somehow prepares some games to run on linux and now kingpin seems to run in single player - but there is no sound. I tried your echo....and so and so and got permission denied!!! Any clue??? and did it with sudo too!!!!('sudo echo 'kingpin 0 0 direct' > /proc/asound/card0/pcm0p/oss')..and got...('bash: /proc/asound/card0/pcm0p/oss: Permission denied')....strange it didn't ask me for a pass??????? Am using Ubuntu 7.04!

---

