---
title: "Volume only works all the way up, or muted"
date: 2006-02-17
forum: Desktop Environments
---

### Post by comet on 2006-02-17
Hi there guys.. My volume doesn't work properly.. Its either BLARING at full volume, or its muted completely...

this happens when I use ANY type of volume control.. Whether its through the main volume control properties in gnome, or through a program like XMMS..

i just want to be able to turn up the volume a little bit.. and it does not permit me to use a soft or medium volume level..

I have a feeling, this same problem is causing movies to have a faint crackling noise in the background.. its very faint, but very annoying.. it happens in ANY media player, with ANY type of movie file.. 

thanks much for your help.. i hope i can resolve this problem.. if it helps, I use an MSI Motherboard, with an Azalea onboard soundcard.. in my bios, it has an option to change the settings to an Ac'97 soundcard.. that might help, if the issue is driver related.. Azalea is pretty much a new type of onboard chipset that may not be fully supported in Linux yet.. thanks again for your time..

---

### Post by gibson on 2006-02-17
Are you using alsa, oss or esd?

I recommend alsa, however, oss may be better for your card.

goto terminal and type > alsamixer and check your levels... i keep mine around 70 (get rid of the red)

hth

---

### Post by comet on 2006-02-25
sorry for the late reply... i ran alsamixer and changed the level down to 70.. no luck.. its still blaring extremely loud, unless I turn the volume down all the way, or mute it.. there's no phaseable volume..

the chipset is C-Media CMI9880, and the card is a HDA-Intel onboard soundcard.. can't quite figure out this issue..

i've done a little research on google about the matter, and there's so many people having the same exact problem with this chipset, and nobody has resolved it yet.. it must be a buggy module..

---

