---
title: "Trouble with Sound Card"
date: 2009-05-06
forum: General Help
---

### Post by ncanna1 on 2009-05-06
Hey, so I installed 9.04 on my old laptop and had the audio working.  However, it wasn't working when I booted it again, so I tried removing pulseaudio, as this is how I fixed my audio issues on my desktop.  I made sure to install esound and all of that to replace pulse, but now it seems that my soundcard isn't being detected.  When I use aplay -l, out comes:

aplay: device_list:217: no soundcards found...

The actual sound card is a Realtek ALC250.  Any ideas on how to detect it?

---

