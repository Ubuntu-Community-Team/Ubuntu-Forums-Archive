---
title: "A question about the ressources CPU used under games on linux and Windows"
date: 2016-03-09
forum: Gaming &amp; Leisure
---

### Post by septicalmind on 2016-03-09
No polemic, just for understand.

On the same machine with ubuntu 15.10 and Windows 7 and three emulators:

PCSX (emulator psone), MAME, emulator of arcade games and DosBOX (emulator MS-DOS).
Pentium D 3,40 Ghz. 2 CPUS is activated on 2 systems. My graphics board uses 2 same drivers owners.

Same exact version of emulators under 2 systems.

The  framerate is slower 1/3 under ubuntu than under Windows. (I know  how  to show the framerate under the various emulators and under dosbox I   used duke nukem 3D - for example and typed DNRATE). For Mame I use the  F11 key and no vsync. I type after the F10 key - So it is on throttle  mode.
Mame and dos box uses only the power of the cpu.

No openGL used with pcsx, If I active it  (on windows and linux) the  framerate is the same : 1/3 slower than windows. The nvidia drivers is  made by nvidia on both systems. I was used no fps limit.

Completely playable under my Linux, but why these works are less quickly than under Windows?

Thank to all to give me answers. Only by curiosity and understand this.

PS: I'm french - so I can't speak better to explain

---

### Post by mastablasta on 2016-03-09
drivers mostly.

even if CPU is used (software acceleration) the GPU is still involved in that it draws the picture on screen.

it then also depends how well software is optimised for the OS. for example some games were reported to work faster under Linux than under Windows. then there were games that worked better under wine than under windows. 

you can also test using Phoronix test suite and select a few demos from it to try under windows and then Linux. however in general the GPU drivers are very close, but are still not as good as in windows.

for example one such Phoronix test: [http://www.phoronix.com/scan.php?page=article&item=nvidia-win10-ubuntu15&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia-win10-ubuntu15&num=1)

you can search for more articles where they compare the drivers onlinux vs windows.

---

### Post by septicalmind on 2016-03-10
Thanks for your answer at my question.
Yes, I understand, drivers mostly...

But,  in pure console mode (without X-window - it is not loaded) : the video  driver is simply vesa... same as dos... no big differences (no?).
The framerate is slower too than under pure dos.
I don't understand why. The core of the linux system is not optimised for this ? By security ?
Many thanks for your answer.

Yes, I know it is not really important... just for learn.

---

### Post by mastablasta on 2016-03-11
I never tried that. 

to test is out you would need to install ubuntu minimal, then dos box and make sure nothing regarding x-window get's installed. then see if DOS box would actually start am not sure how dosbox works in Linux however it is an emulator and as such it could be that it starts an X-window. i don't think dos box would work directly form DOS either. i guess this could be tested maybe with free dos or original do sin virtualbox (if it even supports it). but i suspect it needs windows drawn.

personally i haven't seen any issues, though i never measured FPS and compared. i just know that on my old PC dos games run as smoothly as they would under original DOS.

also the average FPS is not the only measure one should look at.

---

### Post by septicalmind on 2016-03-11
I have just tested under the pure console mode M.A.M.E. in command line.  NO dosbox all right - it need X-window to play. But mame, not.

---

### Post by mastablasta on 2016-03-14
and mame is still slower than in windows?

---

### Post by septicalmind on 2016-03-14
Yes it is.
I repeat : with the same PC with a linux partition, dos  6.22 partition, and windows 7 partition. It is strange isn't it ? I  think the linux core is optimised for working (security) behind and it  cannot be in real time for applications.
So this is not the videos drivers fault.

That is the way it is.
Microsoft's  systems as be made to privilegiate applications before security... And  we can see the result today... Windows is a gaming console. But his time  is ending... again for a little time.

It's that I think.

It is resolved, the post ?
Thanks

---

### Post by mastablasta on 2016-03-15
I don't think this is it. 

it could be that the dosbox code and mame code is more optimised for windows. or simply that the measurement is wrong. 

if all would be well the result should be quite close.

---

### Post by septicalmind on 2016-03-15
The measurements is not wrong.

The mame executable is not  optimised for windows. It is compiled for linux. DOSBOX runs under only  in x-window system mode. This is not a good exemple, because the drivers  can be differents.
But mame not. It is strange, I know. But no problems, Linux is better for all.

If you don't want to believe in me, make the test yourself.

You know, it is not really important... just fun to compare.

---

