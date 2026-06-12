---
title: "Sound Distorted and amarok not playing"
date: 2006-07-07
forum: Desktop Environments
---

### Post by jerinjoy on 2006-07-07
I'm running Ubuntu 6.06 on my laptop. 
two problems:
1. The sound I get from xmms is distorted. Any idea what could be causing this? Its not a problem with my speakers since I tried with headphones also.
2. I installed amarok from synaptic. I can see my music files in the playlist. When I click play it just skips over the songs displaying the name and duration of the track in a popup. Anything I need to install to get it to play mp3's?

---

### Post by jerinjoy on 2006-07-07
Does anyone know what the problem could be? any help would be appreciated.

---

### Post by TheMono on 2006-07-07
Have you already installed the non-free codecs? If not, or if you don't know what I just asked, run Automatix for MP3 support. If you have already done that, I don't know lol.

Second off, I don't know why, but Ubuntu doesn't like sound set high on your computer. I can't turn it above 60%ish without it clipping. If you turn it down, and your speakers up, it should be fine at the same effective volume.

---

### Post by jerinjoy on 2006-07-07
thanx. that solved the problem. I thought the mp3 support was already in since xmms was playing them fine. About the distortion I'm not sure what's causing it.
The automatix caused another problem. When I installed the video and audio codecs the videos are playing too bright. seems like other people have had the same problem too.

EDIT: The distortion is gone with the new codec. I guess the version that comes with xmms has problems.

---

### Post by Bloch on 2006-07-07
I can confirm that I had problems with crackling sound on xmms when playing mp3s. Other programs played mp3s clearly.

---

### Post by PriceChild on 2006-07-07
I would DEFINATELY advise people to install codecs usign the guide:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

instead of automatix or easyubuntu. Because, you can understand what you're installing, and everything gets done properly, you can't quite be sure what's in automatix's code.

Pricey

---

### Post by oncemore on 2006-07-07
try to lower PCM in alsamixer ;)
it should do the trick.

the problem with amarok i dont know...try to upgrade to the last version:
check this: [http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

---

### Post by jerinjoy on 2006-07-08
i should have installed reading the Restricted Formats page. I did that the last time for Breezy. 
Anyways, things are working fine now. The crackling sound is only in xmms but amarok plays fine. the video brightness problem is gone after I restarted?! :)

---

