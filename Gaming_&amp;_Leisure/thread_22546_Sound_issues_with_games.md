---
title: "Sound issues with games"
date: 2005-03-28
forum: Gaming &amp; Leisure
---

### Post by MrGrumpy on 2005-03-28
Ok had a search of the forums and theres a lot of info with regard sound problems, so here goes with my tales of woe. I installed Enemy Territory no probs but I`m getting no sound out of it, the following is the error message /dev/dsp: Cannot allocate memory  now I`m running a Gigabyte NForce 2 board, now my understanding is that nvidia uses OSS for sound and not ALSA which seems to be what the other guides on here seem to lean towards, so I suppose does anyone have any ideas how to get this working or otherwise. I should say sound on the desktop works as does the various media players, just games is a no go !!

Ali

---

### Post by Slalomsk8er on 2005-03-31
```
$ killall -9 esd
$ /usr/local/games/enemy-territory/et

```

This works for me ;)

---

### Post by PsyberOne on 2005-03-31
What I've found is to chown /dev/dsp to your user name, it's ugly but it works for me (maybe some kind of script to set that on login)

---

### Post by bruce89 on 2005-04-06
What I did was go to Synaptic and installed libsdl1.2debian-all and uninstalled libsdl1.2debian-oss.  This fixed all the sounds in Tuxracer anyway.

---

### Post by arrizaba on 2005-04-08
But, do you have to do:

$ killall -9 esd

everytime you want to play?

Is there a way of turning off esd from Hoary by default and use ALSA?

---

### Post by Raven-sb on 2005-04-08
[QUOTE=Slalomsk8er]```
$ killall -9 esd
$ /usr/local/games/enemy-territory/et

```

This works for me ;)[/QUOTE]


It works with me too.  However I am wondering what is causing the problem with the sound, and is there a way of resolving it so that sound for games is accessable without having to enter the command.

Edit:  Many thanks Bruce89,  your post resolved my sound problems with Battle for Wesnoth.

---

### Post by digby on 2005-04-08
What really interests me is why my sound in Cedega (4.3) seems to work so intermittently. The only game I have installed with it is Warcraft III. Sometimes I will start it and get an error that the sound could not be initialized. Sometimes it's persistant; sometimes I can close it and re-open, and it will be fine.

edit: comma splice

---

