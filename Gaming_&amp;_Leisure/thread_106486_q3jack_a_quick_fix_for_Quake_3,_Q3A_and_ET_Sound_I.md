---
title: "q3jack: a quick fix for Quake 3, Q3A and ET Sound Issues"
date: 2005-12-20
forum: Gaming &amp; Leisure
---

### Post by f1d094 on 2005-12-20
q3jack is a small piece of software written by Dmitry Baikov as a workaround for the OSS mmap direct access issue.

In short, it hijacks /dev/dsp mmap calls and outputs the sound via jackd instead.

Unfortuneately, the developer's website has been offline for some time and this solution has been buried in the depths of google...with the author's permission, I have created a mirror of the original site here:

[http://www.craknet.net/q3jack](http://www.craknet.net/q3jack)

When I have time, I will write a formal HOWTO based on my experiences.

Specifically, I am running Q3A in a 32bit chroot on an AMD64 nForce3 Mobo; which has a Realtek ALC850 sound chip. One anomaly remaining...I have to run jackd, q3jack and quake3 all as root:

```

*root@32bitChroot~#* jackstart -R -d oss &
*root@32bitChroot~#* q3jack quake3 +fs_type q3ut3

```

Cheers




Keywords: AMD64 Quake3 Q3A OSS Alsa mmap ubuntu debian realtime latency jackd sound urbanterror urt ut3 q3

---

### Post by wildchild on 2006-03-19
Hey,

as a normal daily user, start jackd without the -R, this allows you to run quake3 also as a user.

---

### Post by GameGod on 2006-03-19
Kick-*** fix! Good job digging this one up! :)

If you don't need punkbuster, you could also give the [Icculus.org Quake3]("http://icculus.org/quake3/") client a shot (it uses ALSA, works nicely), but that only helps you for Q3A...

---

### Post by EPOX123 on 2006-06-28
Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

### Post by th3t1nm4n on 2007-03-30
I made a .deb
I believe it required jackd, libjack-dev, libsamplerate0-dev, and libsamplerate0.

---

### Post by Phantom784 on 2007-04-09
I tried using jackd and joss to get my quake3 audio to work, but jackd keeps giving me errors.

```
**** alsa_pcm: xrun of at least 0.022 msecs



**** alsa_pcm: xrun of at least 0.039 msecs



**** alsa_pcm: xrun of at least 0.054 msecs



**** alsa_pcm: xrun of at least 0.027 msecs

delay of 32806.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32811.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32833.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32833.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32831.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32080.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32818.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32078.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32081.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32082.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32081.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32815.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32814.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32075.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32064.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32081.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32821.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32079.000 usecs exceeds estimated spare time of 1328.000; restart ...


**** alsa_pcm: xrun of at least 0.033 msecs

delay of 32047.000 usecs exceeds estimated spare time of 1328.000; restart ...
delay of 32852.000 usecs exceeds estimated spare time of 1328.000; restart ...

```it keeps repeating these sorts of error messages as soon as i run it.  i'm invoking it with "jackd -R -d alsa -d hw:0 -p 64 -r 48000" as suggested by [http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html)  I tried running it with and without sudo, but still get the errors.

---

### Post by fakie_flip on 2007-04-19
I am using amd64 bit Ubuntu. I am trying to use jack and joss for the game Legends. I have sound in the game, but when I use Skype or Teamspeak, the game has no sound, and then it exits after trying to join a server. As root, I did this just like this FAQ says to.
[http://www.goteamspeak.com/index.php?page=faq&id=3&item=43#q43](http://www.goteamspeak.com/index.php?page=faq&id=3&item=43#q43)

```
echo 'LinLegend 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'LinLegend 0 0 disable' > /proc/asound/card0/pcm0c/oss
echo 'LinLegend 0 0 disable' > /proc/asound/card0/pcm1c/oss 
```

Still after starting the game, it is using /dev/dsp.

```
root@ubuntu:/home/chris/Desktop# lsof | grep dsp
LinLegend 6271      chris   14w      CHR               14,3               13901 /dev/dsp
root@ubuntu:/home/chris/Desktop# 
```

```
root@ubuntu:/home/chris/Desktop/joss-0.3# jackd -R -d oss &
[1] 6622
root@ubuntu:/home/chris/Desktop/joss-0.3# jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
oss_driver: /dev/dsp : 0x10/2/48000 (4096)
oss_driver: indevbuf 4096 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)

root@ubuntu:/usr/games/legends# joss ./runlegends
root@ubuntu:/usr/games/legends# ERROR: ld.so: object '/usr/local/lib/joss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/lib/libdl.so.2' from LD_PRELOAD cannot be preloaded: ignored.
Alert: Error Unable to initialize SDL.  (Error: No available video device)
Exiting

root@ubuntu:/usr/games/legends# file /lib/libdl.so.2 
/lib/libdl.so.2: symbolic link to `libdl-2.5.so'
root@ubuntu:/usr/games/legends# file /lib/libdl-2.5.so 
/lib/libdl-2.5.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), for GNU/Linux 2.6.0, stripped
root@ubuntu:/usr/games/legends#
```

I even tried running jackd like the website says to, but I still got the same errors when trying to load the game with joss.
[http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html)

```
root@ubuntu:/home/chris/Desktop/joss-0.3# jackd -R -d alsa -d hw:0 -p 64 -r 48000 &
[1] 6560
root@ubuntu:/home/chris/Desktop/joss-0.3# jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|64|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 64 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback

root@ubuntu:/home/chris/Desktop/joss-0.3# 

**** alsa_pcm: xrun of at least 0.423 msecs


root@ubuntu:/home/chris/Desktop/joss-0.3# 

**** alsa_pcm: xrun of at least 0.423 msecs



**** alsa_pcm: xrun of at least 0.424 msecs



**** alsa_pcm: xrun of at least 0.420 msecs

jackd -R -d alsa -d hw:0 -p 64 -r 48000 &

**** alsa_pcm: xrun of at least 0.421 msecs
```

---

### Post by fakie_flip on 2007-06-08
bump!

---

