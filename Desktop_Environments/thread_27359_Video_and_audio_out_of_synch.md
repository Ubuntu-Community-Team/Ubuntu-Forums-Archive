---
title: "Video and audio out of synch"
date: 2005-04-15
forum: Desktop Environments
---

### Post by Marble2 on 2005-04-15
Okay, here's what's going on. The audio is 2-3 seconds behind my video in any file I play, any format, and player. I'm using hoary now, but this also happened in warty. It's annoying as hell, and I really want to get it fixed.  I have an ati radeon 9200 sapphire and a Shuttle AN35N ultra mobo using the onboard sound.

---

### Post by medgno on 2005-04-15
If you use mplayer (through the gmplayer frontend is reccomended) you can use the + and - keys to adjust the audio offset. I've found that I've just memorized the offset for the various files that I play most often.

---

### Post by Marble2 on 2005-04-15
[QUOTE=medgno]If you use mplayer (through the gmplayer frontend is reccomended) you can use the + and - keys to adjust the audio offset. I've found that I've just memorized the offset for the various files that I play most often.[/QUOTE]
Well I have mplayer, but I don't use it often. What you suggested did fix that, but it seems like kinda a hack job, and I don't want to have to adjust it every time I open a file.

---

### Post by Marble2 on 2005-04-16
Bump.

---

### Post by Marble2 on 2005-04-18
Bump, anyone have a solution? This is really damn annoying :(

---

### Post by Marble2 on 2005-04-26
I feel like a dick for bumping this again, but I got the fglrx drivers for my ATI card and now the lag is still there, but only very slight. (Or maybe I'm just getting used to it, I dunno.) I've searched around and still haven't been able to find a solution to this. Does anyone know what's wrong?

---

### Post by NeoChaosX on 2005-04-26
Um, how is your audio set up in MPlayer? Are you using ALSA or ESD output? I've found that using ALSA output instead of ESD fixes audio sync problems I had with some files.

---

### Post by Marble2 on 2005-04-26
[QUOTE=NeoChaosX]Um, how is your audio set up in MPlayer? Are you using ALSA or ESD output? I've found that using ALSA output instead of ESD fixes audio sync problems I had with some files.[/QUOTE]
Hmm, now mplayer just freezes when I choose alsa as the output.

---

### Post by NeoChaosX on 2005-04-26
Try the instructions in [this link](http://ubuntuguide.org/#configuresoundproperly) and see if it works then.

---

### Post by Marble2 on 2005-04-26
[QUOTE=NeoChaosX]Try the instructions in [this link](http://ubuntuguide.org/#configuresoundproperly) and see if it works then.[/QUOTE]
Nice, I did that and it works perfect now. Well almost perfect. I get sound in Totem-Xine, but mplayer can't get sound when I set it to either esd or alsa. amaroK also doesn't get sound. How can I get this working?

edit; got amarok to have sound by using output as xine engine, but there is no such option in mplayer.

---

### Post by MrBrownstone3g on 2005-04-27
Hi mate,
           You can select the audio engine mplayer simply follow the instruction below:

Right Click on the MPlayer main window.
Select Preferences.
Click OK  on the popup Window.
Goto Audio tab and select your desired Audio Engine.

---

### Post by Marble2 on 2005-04-27
[QUOTE=MrBrownstone3g]Hi mate,
           You can select the audio engine mplayer simply follow the instruction below:

Right Click on the MPlayer main window.
Select Preferences.
Click OK  on the popup Window.
Goto Audio tab and select your desired Audio Engine.[/QUOTE]
Hey, I've been doing that, but there isn't an xine engine listed there.

---

