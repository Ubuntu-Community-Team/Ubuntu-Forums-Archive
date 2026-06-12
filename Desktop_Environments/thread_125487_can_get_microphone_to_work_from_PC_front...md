---
title: "can get microphone to work from PC front.."
date: 2006-02-04
forum: Desktop Environments
---

### Post by zeltak on 2006-02-04
Hi all

I have an Asus p4p800 Board with a soundmax internal sound card. in Windows after installing the drivers i was able to use the back outputs for my surrond 5.1 setup and use the front outputs (on the front of the PC near the usb outputs) for my Mic/Headphone in order to use with skype. I can get it to work at all under Kubuntu :( . I understand that Soundmax dont have any drivers for linux and they use Alsa. Does anyone know how i can get the front panel outputs to work? i hate switching back to my windows bootup everytime i want to use skype (It aggrevates me seeing the windows logo now LOL...).

thx alot in advance!!

Zeltak

---

### Post by sciawonrose on 2006-12-22
Hello Zeltak

Well your post is almost one year old and I am guessing you solved the problem..how?
I have soundmax as well with an asus a8n-vm csn and would like to use front connectors as well.
The rear ones works well and my front sound output also, the mic does not.

Merry Christmas!!!!!

---

### Post by zeltak on 2007-01-03
hi

Although my post is a year old i havnt solved the problem:( ...I Love Linux and have been using it for more them a year now yet one things that drives me MAD in ubuntu/kubuntu (or maybe its linux...i havnt tried other distro's) is sound issues. especially the microphone support. I havnt been able ever to get my microphone to work even though i changed a motherboard and 3 sound cards through this year!! I hope you manage somehow and if you do please share the info, im about just given up on it!

Zeltak

---

### Post by cblanquer on 2007-01-05
Hi,

I have a P4C800 and front sound input does not work either (dapper, edgy). The rear micro entry is however fine. Maybe ASUS has an issue in that mobo design ?

Regarding my old Thinkpad laptop I cannot get any microphone working, either internal or plugged, I do think laptops are a bigger issue for Linux&sound devices.

---

### Post by teaker1s on 2007-01-05
it's alsa I believe, I have different hardware, same issue and downloading and compiling latest ALSA solves it

---

### Post by ricardo on 2007-01-06
I have the same problem. I have a barebone Asus Vintage V2-PE2. My Edgy recognizes the audio device as "Analog Devices AD1986A". I can use the microphone in the rear connector, but the front connector don't work.

I tried recompiling Alsa with the latest version, but it doesn't work.

---

### Post by lanig on 2007-02-28
Ricardo,

I envisage buying a Asus Vintage V2-PE2. Apart from the microphone problem, does this system run well under ubuntu ?

TIA

alain

---

### Post by oldnat on 2007-08-19
Hi,

using ASUS A8N-VM CSM with Ubuntu 7.4.

HW is OK, Windows XP is able to record sound from the front mic connector (rear not, assume 6 channel-mode but I don't know how to switch it to 2 or 4 channel mode).

Ubuntu but cannot record, there is no "life" neither in the front nor in the back pink connector...

I tried a suggestion changing the /etc/modprobe.d/sound file, but there is no such file in my system...

Any help appreciated.

Nathalie

---

