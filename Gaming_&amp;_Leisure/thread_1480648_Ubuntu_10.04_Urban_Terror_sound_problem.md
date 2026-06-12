---
title: "Ubuntu 10.04 Urban Terror sound problem"
date: 2010-05-11
forum: Gaming &amp; Leisure
---

### Post by Sea_of_fear on 2010-05-11
Hi,

Just wanted to let you know if you have just installed, or rather unzipped, Urban Terror and the sound doesn't work in Ubuntu 10.04 here is what worked for me.

1. Under System>properties you choose sound and jack up the volume til about 100 %.
2. Enjoy the game.

Sorry if this didn't work for you but it worked for me. 

I am posting this because my sound didn't work and I found no explanation anywhere on how to fix it. I was already looking into replacing pulseaudio with esound and so on but then I thought, maybe I just have to raise the volume and it worked! 

On a different note: I just installed Ubuntu 10.04 dual boot with win7 and it worked like a peach. I missed Linux so much. Browsing and working with many programs is just better with linux. Thanks so much for your work Ubuntu.

---

### Post by ziffolo on 2010-06-01
I am playing UT 4.1 under Ubuntu 9.04, via WINE. Till now the worst problem I am having is that sfx comes about 1 sec later thatn they should. It's pretty annoying in a game where "hearing" is very imporant :)

Any of you got a clue on how to fix this ? I tried to modify something in cfg file but nothing changed.

---

### Post by Cresho on 2010-06-01
ya, totally uninstall pulseaudio.

do this

#gedit ~/.pulse/client.conf
and add "autospawn = no" without quotes

run it.  then if it still sucks like audio delay or slow framerates, you can achieve 100% framerate by totally uninstalling the POS pulseaudio.

#sudo apt-get remove pulseaudio

after this, reboot after each session change you did so it can take affect.  Everything will fall back to alsa and work fine.  The only issue you will notice is gnome desktop will have no audio but you will have audio working just fine like flash, tv, music, everything else will work fine.

this is why i switched to kubuntu.  all i did was

#gedit ~/.pulse/client.conf
and add "autospawn = no" without quote

use
#alsamixer
in terminal for audio control

and i did not need to uninstall pulseaudio.  I think it works better with internal audio than it does with my audigy.  In anycase, I took it down.

---

### Post by rizzeh on 2010-06-01
raising PCM level in alsa mixer seems to eliminate the sound lag in quake based games but adds distortion on peak sound levels. Anyways solved it by getting rid of pulse audio ..

---

### Post by ziffolo on 2010-06-04
Thanks ! I removed Pulse and now it works.

---

### Post by ziffolo on 2010-11-04
back to problems with Ubuntu 9.10 :\ installing pulseaudio and the relative libraries doesn't solve it

---

