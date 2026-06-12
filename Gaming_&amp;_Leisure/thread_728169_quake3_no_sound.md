---
title: "quake3 no sound"
date: 2008-03-18
forum: Gaming &amp; Leisure
---

### Post by etlpkby on 2008-03-18
Hello all,

Yep, it's a old topic, but I cannot get quake3 or wolfenstein to work with sound. This is what I get for quake3

[B]------- sound initialization -------
/dev/dsp: Broken pipe
Could not toggle.[/B]

I'm running:-

. AMD64 x2 Dual core processor 6400+ CPU
. Hardy Heron Alpha6 x86_64
. NVIDIA Geforce 9600 graphic card, beta driver ver: 171_06

According to 'alsamixer' my sound device is:-

. HDA ATI SB
. Realtek ALC883

What I have tried:-

I have /dev/dsp and /dev/adsp - chmod a+rw them, and tried both of them using +set snddevice <device> options. 

No effect.

As root:-

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "quake3-smp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

No effect., (Do I need x86_64 not x86 in the above echo's?)

Changed my sound device in menus "System->Preferences->Sound Preferences" from Auto to OSS (All options except 'Default Mixer tracks' which I left alone.)

With Ubuntu I don't see 'artsd' or 'esd' like I did with Fedora Core (many moons ago) :tongue: I would normally get q3 snd working by killing artsd etc. Not with Ubuntu :(

I've got lib32's installed, but it has no effect whether I precede the "quake3" command with "linux32" or not.

Anyone got any tips / got it working in 64bit Ubuntu ?

---

### Post by etlpkby on 2008-03-18
DOH!

I re-read my post, and tried the echo command without the x86 suffix and it worked!!! 

[B]echo "quake3 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "quake3 0 0 disable" > /proc/asound/card0/pcm0c/oss[/B]

I'm going meditate now :redface:

---

### Post by etlpkby on 2008-03-18
hmmm...except it hangs without repetitive sound glitch when I complete the quake3 intro level :(

---

### Post by etlpkby on 2008-03-18
./quake3 **+set s_musicvolume -1**

fixed it ;)

---

### Post by halogentan on 2008-06-12
This was actually the only way that I was able to get quake3 to properly run with sound on Ubuntu Hardy.

I added those echo commands to the start function in /etc/init.d/bootmisc.sh
--------------
case "$1" in
  start|"")
	do_start
	echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
	echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
	;;
--------------

Then I start the game like the post above:
./quake3 +set s_musicvolume -1


Muchos gracias to etlpkby!

---

