---
title: "Cedega / Call of Duty sound problems"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by rvarma on 2005-08-01
I recently installed Cedega to play some windows-only games, as those are the only reason I boot into Windows anymore. When trying to play Call of Duty however, I run into some problems. I can hear sounds just fine, but sometimes my game will just freeze for a few seconds, then resume. Obviously in a game like CoD, that gets you killed pretty fast.

I know this is a problem with the sound, as disabling sound in Cedega (for example by running BMP when starting the game) fixes the problem and all is well. Except I have no sound. I've followed various guides on this forum to fix this problem, most recently [this](http://ubuntuforums.org/showthread.php?t=32063) one and  [this]("http://ubuntuforums.org/showpost.php?p=254685&postcount=6") one, however the problem persists.

Can anybody help me with this? This is pretty much the only thing keeping me from fully moving to Ubuntu :p

EDIT: It should be noted that playing native games seems to work fine. UT2004 (more specifically the UTXMP mod for it) runs without a hitch. Something that might be related is that sometimes when playing a song in BMP, it will suddenly stop playing, and I have to press "Pause" twice for it to continue

Any help is appreciated.

---

### Post by Hairy_Palms on 2005-08-01
i had the same problem in wc3 but it didnt particuarly bother me, rebooting and the running it before anything else seeemed to fix it, or you can try

fuser -k /dev/dsp
cedega cod.exe   or whatever call of duty is
that kills all other sound before starting the game, i have to do that to play enemy territory and thats native, if that dont fix it im afraid i dont know :(

---

### Post by artinla on 2005-08-01
I was having the same problems with my nvidia onboard sound.  I never found a suitable fix, and finally had to install a pci sblive. I had been plagued with numerous sound issues but now everything is perfect.  I run nearly all the latest games, with no problems.  Other than a little mixer tweak that needs to be done upon installation, I have had similar success with the audigy and audigy 2.

Art

---

### Post by rvarma on 2005-08-01
[QUOTE=Hairy_Palms]i had the same problem in wc3 but it didnt particuarly bother me, rebooting and the running it before anything else seeemed to fix it, or you can try

fuser -k /dev/dsp
cedega cod.exe   or whatever call of duty is
that kills all other sound before starting the game, i have to do that to play enemy territory and thats native, if that dont fix it im afraid i dont know :([/QUOTE]

Yeah someone suggested that in IRC a while back, but unfortunately that doesn't fix it :\

[QUOTE=artinla]I was having the same problems with my nvidia onboard sound.  I never found a suitable fix, and finally had to install a pci sblive. I had been plagued with numerous sound issues but now everything is perfect.  I run nearly all the latest games, with no problems.  Other than a little mixer tweak that needs to be done upon installation, I have had similar success with the audigy and audigy 2.

Art[/QUOTE]

Unfortunately replacing the soundcard isn't an option for me, as I'm running Ubuntu on a laptop (Inspiron 8600).

Thanks for the replies!

---

