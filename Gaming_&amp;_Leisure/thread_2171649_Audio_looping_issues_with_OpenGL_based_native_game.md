---
title: "Audio looping issues with OpenGL based native games"
date: 2013-08-31
forum: Gaming &amp; Leisure
---

### Post by KBD20 on 2013-08-31
Hi,
In most of my OpenGL based games (have experienced this problem in the native steam version of L4D2, and the local native version of Dear Esther, I think this affects other OpenGL games, however these are the only 2 I know for a fact this happens to), after a few minutes of playing, I experience the sound 'freezing'. 

The audio within the 1-2 seconds of it freezing begins looping, the way the issue behaves seems to override the system until the games are closed (volume control, muting etc. responds to my commands, however the game audio continues at the same volume). 
This hasn't happened to any other tasks such as playing music and videos, and I have never experienced this with games such as Super Meat Boy or Binding of Isaac (both are windowed and 2d, the other runs in flash only).

To test I have ran Dear Esther via terminal (to see if it gives off any error codes), however it seems that the problem did not occur when playing in terminal for around the same amount of time to trigger the audio issue. 

Has anyone else experience this sort of issue before, and is there any way around this (other than running them via terminal)?

I am currently running: (In case any of these are the cause behind this)
OS: Ubuntu 13.04
Memory: 3.9GB
Processor: Intel® Core™2 Quad CPU @ 2.66GHz × 4 
Graphics: VESA: BARTS
Graphics Card: AMD
OS Type: 32-bit

Thanks in advance;

---

### Post by oldrocker99 on 2013-09-02
You might try installing a different DE; try lubuntu-desktop or xubuntu-desktop, razor-qt (all are in the repositories) or google "MATE desktop" for installation instructions. Many people have had some iffy results with the Unity desktop, while other people love it and use nothing else. Other desktops do use fewer system resources; I have a 2GB RAM Acer C7 Chromebook running LXDE, and I can run OpenGL games with no problems. I'm also a crusty old fart who doesn't like Unity...

---

### Post by KBD20 on 2013-09-03
Hi,
Switching from Gnome Fallback (no effects) to MATE Desktop seems to have solved this issue, and a few other issues I have had with other games (menu-bars crashing, and requiring me to restart X).
However when running MATE desktop the only program I am unable to run is Skype (running through terminal works), do you happen to know if there is a way around this?

Thanks;

---

