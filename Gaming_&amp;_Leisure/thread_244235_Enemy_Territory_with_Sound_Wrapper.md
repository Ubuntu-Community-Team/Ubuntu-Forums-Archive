---
title: "Enemy Territory with Sound Wrapper?"
date: 2006-08-26
forum: Gaming &amp; Leisure
---

### Post by TrendyDark on 2006-08-26
I've tried running ET using three different wrappers.

1)Alsa-oss (aoss)
2) esddsp
3) artsdsp

aoss works, to an extent. If I run ET using aoss I don't get sound, I get this weird noise and I can sort of hear sounds threw it, but it's like having a conversation next to a jackhammer. :D

I read somewhere that ET uses memory mapping for sound. So I used this option when trying out artsdsp and esddsp (artsdsp -m, esddsp --mmap).

This failed horribly, ET wouldn't start.

I'm all out of ideas. I'm trying this because, supposely, I'm supposed to be able to run ET and TeamSpeak using a sound wrapper on my cheap chipset. TS works great with artsdsp, doesn't work with esd or aoss. . .(which i've read numerous places that aoss is supposed to work with TS. . . :()

Any ideas?

---

### Post by KrakensDen on 2006-08-29
Edit: Solution here:
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

```

sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

```

Then you should be able to run the game without the use of aoss, and the sound appears to work fine :).

You'll have to do this every time you reboot, so putting it in your initscripts would be good.

---

### Post by pharcyde on 2006-08-30
You could try using the joss wrapper.  A lot of people have had success with it.  Check it out at [http://www.craknet.net/joss/](http://www.craknet.net/joss/)

---

### Post by qrm on 2006-08-30
so using sound wrapper would let me use some voip programs and ET simultaneously?

---

### Post by fakie_flip on 2007-01-22
Did anyone get ET to work with sound? Mine was working but now I do not have sound anymore. I do not know what made it quit working. I had to run this command to get sound working.

sudo 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

---

### Post by SBFC on 2007-03-04
Mine worked when doing > You'll have to do this every time you reboot, so putting it in your initscripts would be good..

I'm just wondering what scripts that would go in? I guess I dont' know which scripts run as root when the system starts up.

---

### Post by fakie_flip on 2007-03-04
I made a script and named it start-et. Then I used alcarte menu editor to make Wolfenstein from the gnome menu run the script instead of the command et. The script has to be made executable with chmod u+x scriptname. This script checks to see if the sound has already been fixed, and if it hasn't, it fixes it. It uses gksu instead of sudo so that you can use the script from the gnome menu because you won't see it running in a terminal window, so you can't use sudo. The sound fix needs to be done each reboot, and this script does it. I have another script for RTCW that fixes the sound and also stops the screensaver from trying to come on during the game.

```
#!/bin/bash
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0p/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 direct\" >> /proc/asound/card0/pcm0p/oss'"
fi
if [[ ! $(grep 'et.x86' /proc/asound/card0/pcm0c/oss) ]]; then
 gksudo "bash -c 'echo \"et.x86 0 0 disable\" >> /proc/asound/card0/pcm0c/oss'"
fi
et
exit 0
```

---

### Post by SBFC on 2007-03-04
Thank you very much for that script fakie_flip, it works perfectly.

Much thanks.

---

### Post by Phenax on 2007-03-04
I think he posted here somewhere, but here is a "hack" to truly use ALSA with Enemy Territory.
[http://forums.gentoo.org/viewtopic-t-539999-highlight-enemy+territory.html](http://forums.gentoo.org/viewtopic-t-539999-highlight-enemy+territory.html)

---

### Post by j.miller565 on 2007-03-04
Man fakie_flip, you're a genious

---

