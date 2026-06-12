---
title: "Flash player"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Stone123 on 2006-06-05
Ok , tryed troubleshooting tips on ubuntu wiki with esd lib and all that , it didn't work, I am a member of audio group and i tryed stoping esd and the rest of apps using sound card. It didn't give any sound to flashplayer. 

Anyway i can run flashplayer in sudo firefox and there is sound , i also gave chomod acess of 666 to /dev/snd . So what to try next?  ](*,)

---

### Post by brin on 2006-06-05
Hi, do a search on the forum for "flash sound". Lots of people have had similar problems and there is a variety of solutions.
I fixed mine by simply installing the esound-clients package with apt-get. I believe that you do not need to chmod /dev/snd if you use esd as the sound server. As flashplayer will send its audio output to esd instead.

---

### Post by Stone123 on 2006-06-05
[QUOTE=brin]Hi, do a search on the forum for "flash sound". Lots of people have had similar problems and there is a variety of solutions.
I fixed mine by simply installing the esound-clients package with apt-get. I believe that you do not need to chmod /dev/snd if you use esd as the sound server. As flashplayer will send its audio output to esd instead.[/QUOTE]

Thank for trying to help but no i have esound-clients and i have tested with esd in gstreamer-properties , and i did search the forums. I ll just wait for someone else with similar problem.

---

