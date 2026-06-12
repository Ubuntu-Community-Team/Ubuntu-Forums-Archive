---
title: "Enemy Territory -- USB Sound"
date: 2006-11-25
forum: Gaming &amp; Leisure
---

### Post by Peyton on 2006-11-25
Hey, all,

I'm on Ubuntu 6.06, and today I decided to try gaming with Linux. So, I downloaded and installed Enemy Territory. Everything went fine, except there's no sound in-game.  I'm actually using a USB headset (I had to disable my on-board sound in order for sound to work in other applications), and I tried the *echo "et.x86 0 0 direct > /proc/asound/card0/pcm0p/oss* workaround. Linux didn't like "card0", and I'm assuming this is due to the headset, and so I tried replacing "card0" with "card1", "card2", "card3" and "Headset". However, nothing worked.

Does anyone have a solution?

Peyton

---

### Post by xenoalien on 2006-11-25
I have that problem when another program is useing my sound device. I can only have one program run at a time when it comes to useing sound. Such as a video and a snes game. Even when the video is paused I get no sound out the the snes game.

---

### Post by Peyton on 2006-11-25
It looks like Unreal Tournament 2004 isn't giving me any sound either. If someone finds a solution, I'll expand Ubuntu's partition. :)

---

### Post by fatsheep on 2006-11-25
Does this help:

[http://www.ubuntuforums.org/showthread.php?t=254397&highlight=gaming](http://www.ubuntuforums.org/showthread.php?t=254397&highlight=gaming) ?

---

### Post by Peyton on 2006-11-25
As much as I wanted it to work, no. :( 

Oh, and here are the messages I get:
[QUOTE=ET]------- sound initialization -------
/dev/dsp: No such device
Could not open /dev/dsp
[/QUOTE]
[QUOTE=UT04]open /dev/[sound/]dsp: No such device[/QUOTE]

---

### Post by fatsheep on 2006-11-25
> **Peyton said:**
> As much as I wanted it to work, no. :( 

Oh, and here are the messages I get:

1.  Are you using the ET startup script?  If not then what are you using?
2.  Are a Kubuntu or a Ubuntu user (KDE or GNOME)?

---

### Post by Peyton on 2006-11-25
No, I'm not using the startup scripts for either of them. Rather, I'm just entering the commands in the console. I've tried running the games both on KDE and on GNOME (with the difference between esd and artsd noted).

Update:

I finally got sound working by doing a bit of renaming. Maybe I'm wrong, but I think that my headset is */dev/dsp1*, and the game is looking at */dev/dsp*. Either way, it works:
```
sudo mv /dev/dsp /dev/dsp0
sudo mv /dev/dsp1 /dev/dsp
sudo killall artsd; et
```
However, this is a nasty hack. Is there anyway to make my headset */dev/dsp* by default?

---

### Post by karbrino on 2007-02-01
help on this! I using USB Headphone, I wonder how can I make my ET use my device 1 not device 0?

---

### Post by MarkM on 2007-02-15
> **karbrino said:**
> help on this! I using USB Headphone, I wonder how can I make my ET use my device 1 not device 0?

change this line in your config file (in game autoexec.cfg)

seta snddevice "/dev/dsp1"   //dsp is default , dsp1 is headset

---

