---
title: "Soundblaster Live! CT4760 Digital out"
date: 2005-12-24
forum: General Help
---

### Post by Zio84 on 2005-12-24
Hi!
PCM through the digital out jack has stopped working on my Soundblaster Live! CT4760, and I havn't a clue on how to get it working again.
It stopped working after i watched a DVD using gxine with the AC3 pass through option. When i closed gxine the sound mode didn't go back to PCM, it just went from Dolby Digital to nothing. I can still get Dolby Digital mode when using gxine, but i can't get any other digital sound out of my system.
I've tried rebooting, but when it comes to the line where ALSA Card 0 is started the PCM indicator on my reciever disapears.
Any clues?
Thanks

---

### Post by Zio84 on 2005-12-24
Problem solved.
Sollution was to simply change "alsa_passthrough_device" in the gxine config to iec958 instead of iec958:AES0=0x6,AES1=0x82,AES2=0x0,AES3=0x2, and then start a dvd, and quit gxine. voila! PCM is back :D

*Edit: After a reboot PCM was gone again, until I started gxine and played a DVD like before. Solution was to store the current alsa settings with "sudo alsactl store". Now my settings persist after reboots*

---

