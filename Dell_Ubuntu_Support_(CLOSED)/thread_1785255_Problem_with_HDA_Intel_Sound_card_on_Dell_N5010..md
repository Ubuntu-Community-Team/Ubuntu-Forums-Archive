---
title: "Problem with HDA Intel Sound card on Dell N5010."
date: 2011-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vishnu.vyasan on 2011-06-18
Hi Guys,

I am having a Ubuntu 11.04 installation on Dell Inspiron N5010 laptop with a HDA Intel sound card. 

The problem i am facing is that the sound output when i use a headphone is very low. I checked in alsamixer and increased the volume to max still no increase in sound.

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

i tried the above link and modified the /etc/modprobe.d/alsa-base
file with following values.

options snd-hda-intel model=dell
options snd-hda-intel model=basic
options snd-hda-intel model=auto

All these options failed.  Can anyone help me to solve this problem please? Which one will be the correct value for my laptop? 

I never faced this problem with the previous release of ubuntu.

 Thanks and Regards
Vishnu

---

### Post by vishnu.vyasan on 2011-06-19
Guys Please Help!!!!!

---

