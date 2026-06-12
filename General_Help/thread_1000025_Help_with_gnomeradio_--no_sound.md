---
title: "Help with gnomeradio --no sound"
date: 2008-12-02
forum: General Help
---

### Post by 67GTA on 2008-12-02
I have a Hauppauge 1600 card, and the 2.6.27 kernel in Ibex finally has a driver for it(cx18). My TV/radio tuners are initialized at boot. The TV tuner works with Mplayer. The only problem is with no sound in gnomeradio. I don't know enough about how some of the apps interact with the sound card to figure out what is happening. Gnomeradio by itself has no sound. I can listen to radio just fine when using ivtv-radio from the command line. After much Googling, I have managed to get gnomeradio to play sound with the help of aplay. If I open gnomeradio, and then run this command from a terminal ```
aplay -f dat < /dev/video24
``` then I get sound! Is there anyway to combine the two without having to do this every time?

---

