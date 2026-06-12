---
title: "No sound in Enemy Territory"
date: 2010-06-03
forum: Gaming &amp; Leisure
---

### Post by Helios747 on 2010-06-03
Hello,

I play a few games in WINE and a couple Linux native games. Sound works fine in those after I stopped trying to fight PulseAudio and replaced it with ALSA.

My only problem is that Enemy Territory refuses to give me any sort of sound. I have everything on max in the ALSA mixer, nothing is muted.

Ideas?

---

### Post by tankjer on 2010-06-03
Check the Audio/Sound tab (don't remember how it was called) in wineconfig, and check if there's ALSA checked up as audio output.

---

### Post by Helios747 on 2010-06-03
Enemy Territory is a Linux native game.

---

### Post by aeiah on 2010-06-03
is this quake wars enemy territory or the old wolfensteine one? i remember there being an audio issue with the old one, requiring a switch. perhaps the same method will work for the quake wars one

[http://ubuntuforums.org/showthread.php?t=271075](http://ubuntuforums.org/showthread.php?t=271075)

---

### Post by Helios747 on 2010-06-03
Thanks aeiah! That thread fixed it perfectly (FTR it's the wolfenstein one)

> 
in a terminal type: 
Code:
sudo -s 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
exit


to get this commands started after booting automatically: 
open an editor with root rights (gedit) and type 
Code:
#!/bin/sh 
#Bug in Wolfenstein ET 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

save the file as "et-sound" in "/etc/init.d/". after this file is  created you need to tell your system about it: 
Code:
sudo chmod 755 /etc/init.d/et-sound 
sudo update-rc.d et-sound defaults

That worked perfectly.

---

### Post by Noccy on 2010-08-15
> **Helios747 said:**
> That worked perfectly.

Just tried this and it didn't work for me. I get the following:

```
------- sound initialization -------
GETOSPACE: Invalid argument
Um, can't do GETOSPACE?
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/noccy/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/noccy/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/noccy/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/home/noccy/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0x7ba4f40  
Sys_LoadDll(ui) succeeded!
--- Common Initialization Complete ---
```

No sound neither with et or et-sdl-sound, and I've tried terminating pulseaudio etc prior.

Any ideas? And what the heck is GETOSPACE? :o

---

### Post by go_beep_yourself on 2011-08-02
Fails for me. I tried creating the file in vim even, and I wasn't permitted to save it.

"oss" E212: Can't open file for writing

root@ubuntu64 [03:13:17] [~/Desktop] 
-> # echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
zsh: no such file or directory: /proc/asound/card0/pcm0p/oss
root@ubuntu64 [03:13:23] [~/Desktop] 
-> #

---

### Post by deoanam2002 on 2012-01-27
+1. I'm using Ubuntu Studio 10.10. Perhaps there's no oss?

Edit:
Solution: [http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)
I downloaded the script in et-sdl-sound.gz, modified it for the correct directories, and launched the game from there.


> **go_beep_yourself said:**
> Fails for me. I tried creating the file in vim even, and I wasn't permitted to save it.

"oss" E212: Can't open file for writing

root@ubuntu64 [03:13:17] [~/Desktop] 
-> # echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
zsh: no such file or directory: /proc/asound/card0/pcm0p/oss
root@ubuntu64 [03:13:23] [~/Desktop] 
-> #

---

### Post by scania_gti on 2012-02-11
> **deoanam2002 said:**
> ...Edit:
Solution: [http://nullkey.kapsi.fi/et-sdl-sound/](http://nullkey.kapsi.fi/et-sdl-sound/)...
It works! :D
Many thanks :popcorn:

---

