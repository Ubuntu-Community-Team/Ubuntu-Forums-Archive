---
title: "new inspiron 1420 hangs"
date: 2008-07-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ethana2 on 2008-07-23
Ok, I'm trying to figure out what's crashing my new inspiron 1420n so I can get it replaced by dell.

config:
geforce  8400m gs w/ 1440x900 LCD
2.2 GHz C2D, 800 MHz FSB, 4MB L2
bluetooth
2MP webcam
1 GB RAM

The pattern of the crashing is hard to trigger, but now I'm thinking it may be flash.  It doesn't usually happen when I max out the gpu with nexuiz or something..

So I'm in the middle of whatever, and the thing just freezes completely, the sound buffer keeps getting read but not written to or cleared, and these LED's on the thing just start turning on and off and on and off.

I need more reliability than this, can someone help me out?
Also, my dell utility partition is broken and I didn't do it.  So I run their diagnostic and it tests stuff and says 'dell utility partition not ready'.

---

### Post by ethana2 on 2008-07-23
...i've been keeping an eye on all the core temps that i can, and they're always good, the fan works great.  I keep my room very cold and only use my laptop on flat, hard surfaces.

I ran memtest overnight recently and it started to fail around 870 MB.  --but evidently that's not good enough for Dell.  It took hours for it to fail, but again, well ventilated, cold room.

Can I return it over a defective diagnostic partition?

---

### Post by ethana2 on 2008-07-23
Ok, now the machine is off.

4:54:30 - I hit the power button once.
Some LED's light up and flicker and turn back off
The hard drive spins up and the caps lock LED begins flashing.
The optical disk drive LED is on.
Nothing else happens, no LCD backlight, no fan, nada.
~4:55:15 - The machine shuts back off.

It always behaves like this after a hang for a while.  ....but this is much longer than usual.

Ok, I'm calling dell back, this problem is a lot easier to describe than all the other ones I've been having.

---

### Post by Talon2 on 2008-07-23
> **ethana2 said:**
> I ran memtest overnight recently and it started to fail around 870 MB.

If memtest is showing errors then most likely you have faulty RAM.

Write down the details and call Dell Linux/Hardware Support(1-866-622-1947).

---

### Post by ethana2 on 2008-07-23
Right, and I have, but they're not happy with that until /their/ utility tells them its true, and said utility is broken.

Plus, with its refusing to boot, that just doesn't make much sense to me..
I think it may be a bad mainboard, like northbridge or something.

---

