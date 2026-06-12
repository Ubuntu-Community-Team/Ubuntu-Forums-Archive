---
title: "No sound"
date: 2005-07-24
forum: Desktop Environments
---

### Post by newtanker on 2005-07-24
Just installed Ubuntu, and did not notice that the sound was not working (had to do it in another place until i could get ra2500 driver installed so i could update the system)  I have a creative soundblaster live 512 (not exactly sure on the model, its several years old but it does use the emu10k1 driver, ive used it under linux before), and the card is seen in a lspci.  and the emu10k1 is seen in a lsmod.  Problem is, no program can access the card!  alsamixer throws an error, and xmms gives an error message that shows that the interface is either blocked or not configured right.  I was under the impression that ubuntu autodetected these things, but It seems that it doesnt!Anyone have any suggestions????

---

### Post by danns on 2005-07-24
First, what is the error alsamixer is throwing up?  

Do you have a tvtuner card in the system?  Sometimes the tuner card can get configured before the sound card causing applications to sometimes throw up complaints.

In other distros I would use alsaconf in such cases to make sure it was finding my card, but I don't see alsaconf in the alsa-utils for Ubuntu.

I've seen the xmms message come up when xmms was set to use the wrong output plugin.  For instance, if you are in Gnome and the xmms output plugin is set for OSS or Alsa, there could be a problem if ESD is running, thus you probably want to set the output for esound.  If you are not in Gnome or running esd, then you want to set the plugin for Alsa or OSS.

---

### Post by newtanker on 2005-07-24
alsamixer is giving a error of :> alsamixer: function snd_ctl_open failed for default: No such device and i do not have a tuner card in the machine, although i installed everything first then put in the sound card--but that shouldnt make a diff!!

---

### Post by danns on 2005-07-24
Let me step back a minute here.  The emu10k1 is an oss driver, not alsa driver.  So if you are seeing emu10k1 in lsmod you are not running the alsa drivers.  You need to seen snd-emu10k1 for alsa, thus alsamixer is not going to work (no alsa).

That being said, if you are running xmms and are using the output plugin set to alsa, you will get the above error.  Switch to oss and see if that solves the problem.

If that is the case then we can look at getting your card configured for alsa instead of oss.

---

