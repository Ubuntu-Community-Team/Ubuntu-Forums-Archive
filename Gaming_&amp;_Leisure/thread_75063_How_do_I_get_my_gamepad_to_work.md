---
title: "How do I get my gamepad to work?"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by kazuya on 2005-10-13
My gamepad, and I have gotten two of them now, inspite of calibrations done from the control center, and after having installed and ran{executed} jscalibrator, joystick, libjsw, etc, the gamepads do not work. One is a Saitek p880 and the other is some USB gamepad; In the control center, the devices are recognized per their models accurately, it calls the as /dev/js0 and /dev/js1. I saw that I also had /dev/input/js1 up to /dev/input/js4.

How do I get my gamepad to work? I have done calibration from both control center and by running the jscalibrator executable. It says calibration completed. All I did was click a button whenever a prompt came up. I did not actually do any axis movements or moving of the analog D-pads, etc.
Even tuxracer does not work, nor does anything else get controlled by the gamepad. Any ideas?

---

### Post by bdash on 2005-10-13
I have Sega Megadrive-like usb gampad and it worked "out-of-the-box", no installation were required.

In which games are you trying to use your gamepad?

---

### Post by dcarpenter on 2005-10-13
I have a Nyko Air Flo EX and it worked out of the box, no config necessary.  I use it for zsnes and a few other games with no hitches.

I play planet penguin racer with it just fine, i haven't tried the classic tuxracer though, so maybe its just a problem with that specific game?

---

### Post by KingBahamut on 2005-10-13
[QUOTE=kazuya]My gamepad, and I have gotten two of them now, inspite of calibrations done from the control center, and after having installed and ran{executed} jscalibrator, joystick, libjsw, etc, the gamepads do not work. One is a Saitek p880 and the other is some USB gamepad; In the control center, the devices are recognized per their models accurately, it calls the as /dev/js0 and /dev/js1. I saw that I also had /dev/input/js1 up to /dev/input/js4.

How do I get my gamepad to work? I have done calibration from both control center and by running the jscalibrator executable. It says calibration completed. All I did was click a button whenever a prompt came up. I did not actually do any axis movements or moving of the analog D-pads, etc.
Even tuxracer does not work, nor does anything else get controlled by the gamepad. Any ideas?[/QUOTE]

I used to have a p880, and I had success with it, but after a while it just died on me. Now of course I have the Logitech Rumblepad and it works like a charm, out of the box, no conf nessecary.

---

### Post by cfa on 2005-10-13
my gravis gamepad is working like a charm also , just after loading required modules :

sudo modprobe joydev
sudo modprobe emu10k1-gp
sudo modprobe analog
sudo modprobe grip

some time after reboot i've to re create the dev stuff :

sudo rm -f /dev/input/js0
sudo rm -f /dev/js0
sudo mknod /dev/input/js0 c 13 0
sudo ln -s /dev/input/js0 /dev/js0


Anyway it's ok after that !

---

### Post by shawn on 2005-10-13
Dunno if this helps but my system completely ignores jscalibrator, i have to use jscal  in a terminal for it to work. Shame cos jscalibrator has configurable deadzone settings and jscal doesnt seem to have them.

---

### Post by kazuya on 2005-10-26
awesome tips guys. I would try that out. so saitek p880, is not durable?
I guess I have to return this thing then.

---

### Post by Zyphrexi on 2006-03-29
I had gotten that pad to work alright in breezy, now i'm in dapper and there's no worky.

---

### Post by Riskexas on 2011-06-11
Yeah P880 IS PIECE OF BIG AND SHITYFULY BIG ****

---

