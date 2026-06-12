---
title: "Fixed Skype on Kubuntu 9.04 by removing Pulse"
date: 2009-06-05
forum: General Help
---

### Post by wieman01 on 2009-06-05
Hello, 

Just to let you know... This had been a big headache until a few hours ago when I decided to remove Pulse entirely and replace it with ESD:

> sudo killall pulseaudio
> sudo apt-get remove pulseaudio
> sudo apt-get install esound
> sudo rm /etc/X11/Xsession.d/70pulseaudio
Then reboot the PC.

Just in case anybody is in the same situation. Very simple fix, but very effective.

---

