---
title: "STEAM Works! Sorta"
date: 2007-09-04
forum: Gaming &amp; Leisure
---

### Post by Cpl Headshot on 2007-09-04
Hello. I've gotten my games to run, but get no sound and less than acceptable performance. When I go into winecfg I get

libGL warning: 3D driver claims to not support visual 0x4b

and this when I hit the audio tab.

ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:556:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:556:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

CS 1.6 worked well but with no sound and just crashed out of nowhere while DOD 1.3 runs at a low fps. So does anyone know how to get the games to run nice and this is going to sound real idiotic, but what were the wine nice commands?

---

### Post by cogadh on 2007-09-04
What video hardware do you have and have you installed a 3D accelerated driver for it?
Did you create a custom .asoundrc file? It looks like that output is saying there might be a fault in your dmix config.
There are no wine nice commands, there is only the system nice command. It should be used something like this:
```
nice -10 wine game.exe
```

---

### Post by Kimm on 2007-09-04
I don't know how you did it, but I can run Steam and CS 1.6 without any problems. This was with the standard wine configuration in Ubuntu.

If Ubuntus build doesnt work for you, try WineHQ's, type:

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get upgrade

```

in your terminal.

Note that you _must_ use the OSS Sound Driver in Wine (winecfg -> Audio -> Driver Selection: OSS Driver (make sure this is the one one selected!!)

If sound wount work, kill all media players running (and anything that might make a sound (mute sound in Pidgin)).
If it still wount wok, type this in your terminal (GNOME): killall esd
(KDE): killall artsd

---

