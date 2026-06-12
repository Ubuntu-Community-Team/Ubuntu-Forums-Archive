---
title: "Can't install WoW"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by Tails Prower on 2007-06-03
I've been following the guide here 
[http://ubuntuforums.org/showthread.php?t=312482&highlight=installing+wow+with+wine]("http://ubuntuforums.org/showthread.php?t=312482&highlight=installing+wow+with+wine")
to install World of Warcraft, but i've run into a brick wall. The guide claims that the next step is editing config.wtf, but the file doesn't exist. the website claims that if config.wtf doesn't exist, WoW will create it on running, but when I run 
```
wine "C:\Program Files\World of Warcraft\WoW.exe" 
```
the terminal returns two errors, ad nauseum.

err:dsound:DSOUND_MixOne underrun on sound buffer 0x204b08
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=16384 < primary_done=28224)

Either I'm missing some kind of audio codec or the game won't run in directx. 
Any Ideas? I'm hoping it's some kind of missing audio package, because if directx is the problem...

I can't switch the game from running directX to running OpenGL (because there's no config.wtf), so it won't run, so it won't create config.wtf, so I can't switch the game from running directx to opengl.

---

### Post by Ferrat on 2007-06-03
To use OpenGL just use the switch -opengl if I remember correct

wine wow.exe -opengl 

the sound problem is prolly a wine setting, have you installed ALSA, OSS and AOSS

run winecfg 

go to the sound setting and select ALSA or OSS as primary sound

---

### Post by Tails Prower on 2007-06-03
When I ran
wine wow.exe -opengl
it gave me the 'world of warcraft was unable to start 3d acceleration' error message, and gave some errors in the terminal about dllmain not being fully installed.
I'm looking for some better drivers for my video board (RS482 [Radeon Xpress 200M]), but i hear it's hard to get ATI drivers for linux. Is all linux gaming this frustrating?

---

### Post by hikaricore on 2007-06-03
WoW is not linux gaming.

And yes all linux gaming can be frustrating _ but only with an ATI card_.
AMD is currently working on better drivers and linux support but it may be awhile.

As always I suggest Nvidia if you are even thinking about a change of video cards, or if you have a spare lying around.  ^_^

---

### Post by Sammi on 2007-06-04
> **Tails Prower said:**
> When I ran
wine wow.exe -opengl
it gave me the 'world of warcraft was unable to start 3d acceleration' error message, and gave some errors in the terminal about dllmain not being fully installed.
I'm looking for some better drivers for my video board (RS482 [Radeon Xpress 200M]), but i hear it's hard to get ATI drivers for linux. Is all linux gaming this frustrating?Make sure you are using the closed-source proprietary ATI drivers, the open-source ones are not that great for gaming: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

It's easier to use Envy for installing graphics card drivers though: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I really like Envy. It's a solid program with a good track record.

---

