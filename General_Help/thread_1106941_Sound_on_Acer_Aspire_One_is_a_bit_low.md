---
title: "Sound on Acer Aspire One is a bit low"
date: 2009-03-26
forum: General Help
---

### Post by iareConfusE on 2009-03-26
I've been trying to listen to music on my AAO, and even at max volume, the speakers are still really quiet.  Is there anyway to boost the volume level?

Thanks.

---

### Post by Toddy on 2009-03-26
Try running alsamixer from Terminal.  Check to see if the volume there is set to maximum.

---

### Post by iareConfusE on 2009-03-26
> **Toddy said:**
> Try running alsamixer from Terminal.  Check to see if the volume there is set to maximum.

Yeah did that already, its set to max, but its still quite low.  Could it be a driver issue?

---

### Post by LowSky on 2009-03-26
open the volume controller from the top panel. open volume control from top panel , then go to  Edit > Preferences and tick off all the options. 

then set almost all of them to 100% (dont worry about the mic and line in).

 then go to terminal and type
```
sudo alsactl store
```

that should do it

---

### Post by iareConfusE on 2009-03-27
> **LowSky said:**
> open the volume controller from the top panel. open volume control from top panel , then go to  Edit > Preferences and tick off all the options. 

then set almost all of them to 100% (dont worry about the mic and line in).

 then go to terminal and type
```
sudo alsactl store
```

that should do it

This worked, thanks very much!

---

### Post by DeMus on 2009-03-27
> **LowSky said:**
> open the volume controller from the top panel. open volume control from top panel , then go to  Edit > Preferences and tick off all the options. 

then set almost all of them to 100% (dont worry about the mic and line in).

 then go to terminal and type
```
sudo alsactl store
```

that should do it

Maybe a little explanation on what you wrote is in order. Maybe this way others can benefit from it. What did you do to boost the sound?

---

### Post by blazemore on 2009-03-27
The sound on the Aspire One is awful anyway. I don't think it's a software thing because it distorts at high volumes. If you forced it any higher it wouldn't get louder, just more distorted.
It's enough for system sounds in a quiet room, or some music.

---

### Post by BrainwreckedTech on 2009-06-25
> **DeMus said:**
> Maybe a little explanation on what you wrote is in order. Maybe this way others can benefit from it. What did you do to boost the sound?

By default, Ubuntu hides a lot of options in the Volume Control program to avoid confusion.  Unfortunately this also hides some controls that don't seem important but are, like Front.  To further complicate things, Gnome Volume Control's naming scheme is inconsistent and sometimes flat-out wrong.  The problem with low volume on Aspire Ones just throws an extra whammy out there.

HDA chipsets have an awareness of separate front and back audio connections.  Sometimes, like in the case of the Aspire One, you find an HDA chipset that takes shortcuts.

My Asus A8N-VM mobo with NVIDIA HDA using the Analog Devices AD1986A chipset shows Master/PCM/Headphone/Front, even though "Headphone" refers to the jack provided for front panel audio and "Front" refers to the jacks provided in the back of the motherboard for speakers.  Sound can be played through both ports at separate volumes.

My Acer Aspire One with Intel HDA using the Realtek ALC272 chipset shows Master/PCM/Front.  This is because of the use of HDA.  However, there is no volume control for Back/Headphone, only mute/open.  And when the headphones are plugged in, the speakers shut off.  It's not like Realtek hasn't been caught taking shortcuts before.

---

### Post by FlashDude on 2009-08-04
Actually it would be more accurate to say the onboard speakers on the AAO sucks because if you use a decent set of speakers or earbuds it sounds very good.  The sound quallity in Windows is a fair amount better mind you but the solution above fixed my low volume problem as well. 

Awesome Job Thanks

---

### Post by martinbaselier on 2009-08-04
If you want better sound quality, try OSSv4. I think it can compete quite well with windows, unlike alsa.

---

### Post by speedwell68 on 2009-08-04
> **blazemore said:**
> The sound on the Aspire One is awful anyway. I don't think it's a software thing because it distorts at high volumes. If you forced it any higher it wouldn't get louder, just more distorted.
It's enough for system sounds in a quiet room, or some music.

To be fair I think the sound quality on the AAO is superb when you consider the size of the speakers.  Speaker size is directly linked to sound quality.

---

