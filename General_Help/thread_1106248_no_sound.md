---
title: "no sound"
date: 2009-03-25
forum: General Help
---

### Post by Quicksilver21 on 2009-03-25
i just reformatted my hard drive, im coming from a dual boot with ubuntu 8.10 and xp, and i did the same thing only ubuntu hasnt had any sound since i installed it, no system sounds or anything.
 
Im a pretty big noob when it comes to troubleshooting ubuntu so if anyone can help em get my sound working it would be appreciated.

I have a creative soundblaster audigy2 zs, nothing is muted and everything is plugged in, when i right click on my little sound thing in the system tray and go to preferences i have "Audigy2 ZS [SB0350] (Alsa Mixer)" set to master

---

### Post by evilaim on 2009-03-25
hmm tried making a .asoundrc file in your home folder with settings for alsa?

If i havent made a typo at the settings the following might work (copy this into the .asoundrc) tho its a longshot:

pcm.sound-blaster{
type hw
card 0
}

pcm.sb {
type plug
slave.pcm "audigy"
}

pcm.audigy {
type dmix
ipc_key 1234
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 48000
}
}

ctl.sound-blaster {
type hw
card 0
}

---

### Post by caver1 on 2009-03-25
Try going to your Volume control and under the switches tab see if there is an Audigy Analog/Digital Output Jack choice.
If there is uncheck it and see if you now have sound.
caver1

---

### Post by Quicksilver21 on 2009-03-25
haha thank you, that was it, u guys rock

---

### Post by evilaim on 2009-03-25
*wonders which was it*

---

### Post by Quicksilver21 on 2009-03-25
> **caver1 said:**
> Try going to your Volume control and under the switches tab see if there is an Audigy Analog/Digital Output Jack choice.
If there is uncheck it and see if you now have sound.
caver1

that was it

---

### Post by evilaim on 2009-03-25
Thanks for the reply.  Have a great day.

---

