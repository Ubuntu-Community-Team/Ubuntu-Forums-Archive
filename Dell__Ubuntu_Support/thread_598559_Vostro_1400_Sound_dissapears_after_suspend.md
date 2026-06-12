---
title: "Vostro 1400: Sound dissapears after suspend"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by Skuzniak on 2007-10-31
I have had some issues with getting sound to work on my Vostro 1400 (like most people here). I followed these instructions to some success:

sudo gedit /etc/modprobe.d/alsa-base

and added the line options snd-hda-intel model=3stack

This caused my sound to kind of work. On the login screen I would get sound, but whenever I tried to play audio inside ubuntu, nothing would happen. My speakers are not muted.

I next did the following:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

After performing these commands, my sound worked perfectly, inside ubuntu and at the login screen. My only issue now is that when I suspend my laptop (close the screen) and come back, my sound vanishes. Speakers are still not muted. Rebooting returns the sound.

Any ideas? Thank you.

---

### Post by dmgthe2nd on 2007-10-31
I offer no more solutions but just a tip..
When you boot with something plugged in the headphone jack, the speakers will not work until you reboot but you can get sound out of your headphones.

This is good for those of us that rarely use the laptop speakers.

---

### Post by loopeando on 2007-10-31
Tried it on a Lenovo 3000 N100 (Intel HDA with Analog Devices codec) and it doesn't work.

---

### Post by professor fate on 2007-10-31
try this in your options stack: options snd-hda-intel model=5stack

i see you have a 3.  try 5.

---

### Post by Skuzniak on 2007-11-01
Thank you professor fate, that fixed the issue.

---

### Post by saru411 on 2007-11-01
you should also try restarting xserver (cntr+alt+backspace) rather than rebooting. it is much faster and normally fixes any issues i happen to run into with similar situations.

---

