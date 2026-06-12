---
title: "No Sound in Postal 2"
date: 2007-04-13
forum: Gaming &amp; Leisure
---

### Post by noerrorsfound on 2007-04-13
I am running Ubuntu 6.10. Postal 2 has no sound yet I don't have sound problems in any other games or programs. I was unable to find a solution by searching these forums or Google. One post here said to change sound from Autodetect to ALSA which didn't work, and one said to run "killall esd" in the console which did not work.

---

### Post by MaximB on 2007-04-13
try changing the sound from Autodetect to other then ALSA - it also worked for me.
I mean in your ubuntu sound preferences.
(there is open source sound)

---

### Post by rainbow on 2007-04-14
:KS try the method upstairs mentioned and good luck.

---

### Post by noerrorsfound on 2007-04-14
> **MaximB said:**
> try changing the sound from Autodetect to other then ALSA - it also worked for me.
I mean in your ubuntu sound preferences.
(there is open source sound)
I just tried OSS (Open Sound System) and sadly that did not work, either.

---

### Post by noerrorsfound on 2007-04-14
I found out that I have this problem in Return to Castle Wolfenstein, also.

---

### Post by fakie_flip on 2007-06-06
Weird, I can't even get the game to install. Here is what happens. I tried installing it three different ways, and after each time, I still didn't have the game installed. My games menu in Gnome doesn't show the game. I can't find it installed anywhere, and I can't find any commands to start the game. Any ideas?

chris@ubuntu:~/Desktop$ ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$ 

chris@ubuntu:~/Desktop$ sudo ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$

chris@ubuntu:~/Desktop$ sh postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$

---

### Post by Sockerdrickan on 2007-06-06
> **fakie_flip said:**
> Weird, I can't even get the game to install. Here is what happens. I tried installing it three different ways, and after each time, I still didn't have the game installed. My games menu in Gnome doesn't show the game. I can't find it installed anywhere, and I can't find any commands to start the game. Any ideas?

chris@ubuntu:~/Desktop$ ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$ 

chris@ubuntu:~/Desktop$ sudo ./postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$

chris@ubuntu:~/Desktop$ sh postal2mpdemo-lnx-1407.run 
Verifying archive integrity... All good.
Uncompressing Postal 2 MP Demo for GNU/Linux 1407.......................................................
chris@ubuntu:~/Desktop$
sudo apt-get install libgtk-1.2

---

### Post by Th3Sourc3 on 2007-06-15
I'm having the same problem.  I've got a linux native version of postal 2, it runs fine (except for a bit of slowdown), but has no sound.  I've tried changing to ALSA and OSS, but nothing seems to help.  Any tips?

---

### Post by fakie_flip on 2007-06-25
Certain other programs with sound can not run with the game, or they will cause you to have no sound in the game.

lsof | grep dsp

That will show you what programs are not allowing the game to have sound. Kill those programs, and then run the game. You may also try killing esd.

sudo killall esd

I have Postal 2 running good and even in the 64 bit version of Ubuntu which is more challeging to get programs working. The game is in 32 bit, so I must have all the 32 bit libs for the game, and the game must be able to find them.

---

### Post by ssvt on 2011-05-09
NooB question. How do I kill these?

lsof | grep dsp
pulseaudi 1833      steve  mem       REG        8,6    80720     401309 /usr/lib/sse2/libspeexdsp.so.1.5.0
gconf-hel 1851      steve  mem       REG        8,6    80720     401309 /usr/lib/sse2/libspeexdsp.so.1.5.0


Thanks!

---

### Post by Perfect Storm on 2011-05-10
Thread closed. Necromancing (2007).

---

