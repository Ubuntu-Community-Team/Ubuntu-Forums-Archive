---
title: "Wolfenstein Enemy Territory"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by SecrethX on 2005-11-11
I downloaded the linux install. I installed it and everything went fine. Then I opened it but then it all went wrong. When I opened it gived me a black screen for a couple of seconds and then it crashed. When I opened it via Terminal I got only 1 error (if you can call it that way).

Terminal screenshot: [[IMG]http://img491.imageshack.us/img491/1540/screenshot3on.png[/IMG]](http://img491.imageshack.us/img491/1540/screenshot3on.png)


I hope you guys can figure out whats wrong!


Regards.

---

### Post by cydizen on 2005-11-11
Hi, 

 At first glance it seems that you do not have any hardware acceleration as noted toward the bottom of your screen shot.  What type of card are you using?  Let's start with that and see where it takes us....



Regards,
Bruce

---

### Post by SecrethX on 2005-11-11
nVidia NV17 GeForce4 MX 440

---

### Post by cydizen on 2005-11-11
Okay cool. I am not sure if you are new to Linux or not, but have you installed the nvidia driver? If you are not sure, (you probably didn't) but can you post your xorg.conf in here?

Here is the location of the file:   /etc/X11/xorg.conf

---

### Post by SecrethX on 2005-11-11
I'm very new. I am only into ubuntu (live cd) for a month, and installed it yesterday. I probably didnt install the driver but I'll post my xorg.conf here. 

Its a bit big so I posted it in the pastebin. [http://paste.ubuntulinux.nl/4369](http://paste.ubuntulinux.nl/4369)

---

### Post by SecrethX on 2005-11-11
Ok got it working. But now I dont have any sounds..

---

### Post by Harleen on 2005-11-11
Your sound card is already in use by another program (probably "esd"). Try this:
[http://ubuntuforums.org/showthread.php?t=83416](http://ubuntuforums.org/showthread.php?t=83416)

---

### Post by cydizen on 2005-11-11
booya!  Let us know if the sound fix worked for you...

---

### Post by SecrethX on 2005-11-11
doesnt work. I use SoundBlaster Live! as driver card.

---

### Post by Harleen on 2005-11-11
That card should be able to play multiple sounds simultaniously, so you even shouldn't need to do the "kill esd"-thing.
There's probably some other problem. What output do you get on the command prompt? Especially the part behint "------- sound initialization -------" is interesting.

---

### Post by SecrethX on 2005-11-11
------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaf308000 dma buffer
No background file.
----------------------
Sound memory manager started

But the sound ISNT muted. I dont know why its saying it. Because atm Im listening to music.

---

### Post by Harleen on 2005-11-11
It's OK, that's the same I get. Does it load the shared library afterwards? (no, I don't know if it's important for the sound - just wild guessing)

For me it looks like that:

> ------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaf5c5000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/home/marko/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/marko/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/marko/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xada33f40
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---

---

### Post by SecrethX on 2005-11-11
This is what I got:

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xaf308000 dma buffer
No background file.
----------------------
Sound memory manager started
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such fil e or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xad776f40
Sys_LoadDll(ui) succeeded!
Found high quality video and fast CPU
--- Common Initialization Complete ---

---

### Post by Harleen on 2005-11-11
Strange. I have the same sound card and haven't had any sound related problems yet. I just tried starting amarok, wesnoth ane ET at the same time - worked perfectly. All three applications could play their sound.

You console output also looks good. (except that you are obviously working as root)
In other words: I'm out of ideas, what might go wrong on your machine.

---

### Post by SecrethX on 2005-11-11
I have an actient SB Live!, could it be that the problem is there?

---

### Post by Harleen on 2005-11-11
My card is probably as ancient as yours. ;)
You could try to launch two applications, that use the sound device at the same time to ensure, your sound card can handle it.

---

### Post by SecrethX on 2005-11-11
I can. I'm running beep and Totem at the same time, both are giving music.

---

### Post by SecrethX on 2005-11-11
Got it working. I simple forgot to disable my ONBOARD media shit. Thanks anyways :D

---

