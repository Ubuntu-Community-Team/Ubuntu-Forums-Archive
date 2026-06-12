---
title: "No Sound in Enemey Territory"
date: 2006-03-08
forum: Gaming &amp; Leisure
---

### Post by WillFerrellLuva on 2006-03-08
I just installed et from et-linux-2.60.x86.run and i have no sound.

when i run from a terminal i get the following error:

------- sound initialization -------
/dev/dsp: Invalid argument
Could not set /dev/dsp to stereo=2------------------------------------
Sound memory manager started
Sys_LoadDll(/home/chris/.etwolf/etmain/ui.mp.i386.so)...
Sys_LoadDll(/home/chris/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/chris/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa5a64f40
Sys_LoadDll(ui) succeeded!

I have tried all of the things here: [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)
and none have worked.

Any ideas?

---

### Post by swamytk on 2006-03-08
seems to be there is no device special file /dev/dsp in your system. Pl. find the audio device special file and make a symbolic link to it as /dev/dsp.

---

### Post by WillFerrellLuva on 2006-03-08
I have a "x-special/device-char" file called dsp in /dev.

Is that what you mean?

---

### Post by swamytk on 2006-03-08
yes, u r right. Other multimedia application works? if works, check the audo device file in preference of that application. Find the audio device file.

---

### Post by WillFerrellLuva on 2006-03-08
My sound works in almost everything else (however the sound in planet panguin racer doesnt work unless I killall esd before i run it)

Im new to linux and dont really know how to check the audo device file in preference of that application...sorry

Maybe you could tell me how to go about doing that?

---

### Post by meborc on 2006-03-08
missing sound in ET is an old issue... try to search for it in this forum... i'm sure i have read a couple of threads about it... i just can't remember where... :rolleyes: 

may be this helps: [http://ubuntuforums.org/search.php?searchid=4190253](http://ubuntuforums.org/search.php?searchid=4190253)

---

### Post by soonindallas on 2006-03-08
post #1 in this thread.

works for me.

[http://www.ubuntuforums.org/showthread.php?t=78674](http://www.ubuntuforums.org/showthread.php?t=78674)

---

### Post by equilibrium on 2006-03-09
altho problems with sound with quake3 and enemy terrirory are old, just doing ```
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` will not work in this case as there is no /dev/dsp, meaning oss is probably not setup in the alsa configuration (also meaning  /proc/asound/card0/pcm0p/oss does not exist).
The best thing to do is have a look at the [ALSA website](http://www.alsa-project.org/alsa-doc/) for your soundcard and see what is needed to be done to enable OSS.

---

### Post by WillFerrellLuva on 2006-03-10
Hi,

I tried to look for my sound card info on that site.  I built my computer and know that my sound card is a turtle beach Catalina, but according to the system its showing as a "VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-CHannel Audio Controller"

Neither the catalina or the VIA soundcard is listed on the website though (could it be that the system is using the onboard sound card which i thought i disabled in the bios??).

I tried using the echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss command from a root terminal and then ran tc-elite from a terminal and get the following:

------- sound initialization -------
/dev/dsp: Invalid argument
Could not set /dev/dsp to stereo=2------------------------------------
Sound memory manager started
Sys_LoadDll(/home/chris/.etwolf/tcetest/ui.mp.i386.so)...
Sys_LoadDll(/home/chris/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/chris/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa5a9ecc0
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm


Please help me, tc-elite looks like a cool game and I want to play it (although I think I still like counter-strike better :)

---

### Post by Schmic on 2006-03-12
have you tried this in a terminal?

```
killall esd; et; esd
```

This solution worked for me. I got it from an old post a while ago but I can't seem to find it. Hope it helps.

EDIT: didn't notice you have the link to the wiki that has that option, so you must have tried that already:-#

---

### Post by WillFerrellLuva on 2006-03-12
Hi,

I saw that in a post too and tried it.

However, it didnt work :(

---

### Post by equilibrium on 2006-04-02
I saw somewhere that you can use the CS462xx driver for that soundcard in alsa. I had a Hercules Fortissimo card using this driver and had it working with quake3. Wouldn't work with teamspeak at the same time tho so I got a sb audigy2.

[cs462xx on ALSA site](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Hercules&card=Game+Fortissimo+II.&chip=CS4624&module=cs46xx)

You might have to resort to using artsdsp but I don't remember having to.

---

### Post by WillFerrellLuva on 2006-04-02
Yeah, I did try that and it didnt work.

I pretty much gave up trying to get it to work, and now play UT2004, which is awesome btw.

Thanks for the help though.

---

### Post by SlCKB0Y on 2006-04-03
[QUOTE=equilibrium]altho problems with sound with quake3 and enemy terrirory are old, just doing ```
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
``` will not work in this case as there is no /dev/dsp, meaning oss is probably not setup in the alsa configuration (also meaning  /proc/asound/card0/pcm0p/oss does not exist).
The best thing to do is have a look at the [ALSA website](http://www.alsa-project.org/alsa-doc/) for your soundcard and see what is needed to be done to enable OSS.[/QUOTE]

I had the exact same problem as him. My et was complaining about not being able to find /dev/dsp and the above fixed it. Also turning of esd fixed it but that is a much more messy solution.

---

