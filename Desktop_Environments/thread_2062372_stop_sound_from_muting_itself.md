---
title: "stop sound from muting itself"
date: 2012-09-24
forum: Desktop Environments
---

### Post by bilboubu on 2012-09-24
hi, on xbmcbuntu if there is a crash or something or someone switches of the power while in standby when the computer is switched back on the sound has muted itself.

I can unmute it by running a pactl command but why is it muting in the first place and how do I stop it? thanks

---

### Post by NikTh on 2012-09-24
Try to disable auto-mute in alsamixer , BUT maybe this change creates other problems , like speakers and headphones produced sound together.

---

### Post by bilboubu on 2012-09-24
wow, quick reply thanks! How do I do that, is that "alsamixer" from the cmd line?

edit found how, does it matter that I am running pulse audio?

---

### Post by NikTh on 2012-09-25
> **bilboubu said:**
> 

edit found how, does it matter that I am running pulse audio?

Pulseaudio and alsa are pre-installed in Ubuntu. So I guess no matters. 

If you meant the pulseaudio GUI (pavucontrol) then no , no matters (again) .

---

### Post by bilboubu on 2012-09-25
I dont appear to have an automute when running alsa mixer just 4 s/pdifs?

---

### Post by NikTh on 2012-09-25
> **bilboubu said:**
> I dont appear to have an automute when running alsa mixer just 4 s/pdifs?

Probably not. You must select the correct sound card. 

In alsamixer you can navigate with arrow keys (right-left) and increase or decrease volume with arrow keys(up-down). Also you can mute [MM] or unmute channels with key 'm' . 

If you see up , you will see some keys like F5 , F6 , F3 , it writes what each button do. 

First press F5 so you can see all channels and if nothing appearers press F6 to select the correct sound card.

Look the attached .

---

### Post by bilboubu on 2012-09-26
Thanks for the suggestions but all I can see are the 4 spdifs even when I hit f5 view all and go left and right and select both hda nvidia and default.

---

