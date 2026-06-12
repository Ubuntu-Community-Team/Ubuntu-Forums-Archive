---
title: "Nforce2 drivers and Linux.."
date: 2005-12-23
forum: General Help
---

### Post by floyd27 on 2005-12-23
Hey guys and gals..
 I have a Nforce2 chipset in my mobo. I just noticed the other day that nvidia has linux drivers for this chipset. 
So I have been running for about 6 months now with no problems from not installing these drivers.
Does ubuntu have these drivers already or should I go ahead and install them from the site?


Thanx

---

### Post by wylfing on 2005-12-23
There are people who manage to get these drivers working, but frankly it is a real pain, and there is almost no benefit. The open-source network driver that comes preinstalled with Ubuntu handles the on-board LAN perfectly, and the sound driver from nVidia is OSS instead of ALSA. (If you don't know what that means, the short story is OSS is Linux sound technology from 15 years ago.) Now since the sound chip on your motherboard *probably* can do hardware mixing, you actually can get nVidia's OSS drivers working respectably. However, doing so requires a major investment of time and headache, and the results may only be marginally better (or no better!) than the open source drivers you're already using.

So, forget it. What you get by default with Ubuntu is fine. Use that.

---

### Post by floyd27 on 2005-12-23
Thanx.
i dont have any problems with my system now so Ill just leave it alone..

---

### Post by sciurus on 2005-12-24
[QUOTE=floyd27]Thanx.
i dont have any problems with my system now so Ill just leave it alone..[/QUOTE]

Do you have the onboard surround sound working?

---

### Post by floyd27 on 2005-12-24
yes.

---

### Post by RedLine on 2005-12-25
how? i can't get it working the 5.1 way.

---

### Post by bonzodog on 2005-12-25
RedLine:
Do you have ALSA enabled? Gnome uses esd (esound Daemon) by default, which only handles dual channel. You need to switch the gnome sound driver over to alsa then open the mixer and make sure the rear channels are enabled.

---

### Post by RedLine on 2005-12-25
Yes, i think it's all there but stil not working. I've tryed in other distros to... but with no success. I mention that in windows it works fine.

---

### Post by mcduck on 2005-12-25
[QUOTE=RedLine]how? i can't get it working the 5.1 way.[/QUOTE]
Do you mean live Dolby Digital encoding or analog 5.1? I think that nVidia drivers would enable that.

Myself, I quite like the way the drivers from repos handle my sound. Using ALSA I can set Amarok and Xine to output everything to digital output, and at the same time use analog outputs for everything else. Anyway, I don't don't play any games that would have surround sound, 5.1 in movies works anyway and I get music as PCM stereo instead of lossy Dolby Digital.. This way I can also be sure that no system sounds or sounds etc. play through my amplifier. Only music/movie sounds :)

---

### Post by RedLine on 2005-12-25
i don't know how to configure it. do you know any tutorial?

---

