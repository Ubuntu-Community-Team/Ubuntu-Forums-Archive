---
title: "Low fps in neverwinter nights with ATI"
date: 2006-01-28
forum: Gaming &amp; Leisure
---

### Post by preserved on 2006-01-28
Hi,

I am kinda new to linux but I am a fast learner, I have succesfully installed my Radeon 9800 AIW Pro and Neverwinter Nights but the game is unplayable due to really low fps...

fgl_glxgears show about 900 fps, and flgrxinfo shows the ati driver.

Yours sincerly
Franz - Josef

---

### Post by Horndog on 2006-01-28
Give up the results of fglrxinfo in your terminal just copy and paste.

---

### Post by preserved on 2006-01-28
Here is the info:

preserved@Highspeed:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Oh by the way, the processor and the OS is 64-bits

---

### Post by Horndog on 2006-01-28
This is my info as you can see the fps are very much higher which indicates something is broken in you current setup. 
I'm using the 32bit K7 Kernel. You might try the newest ATI drivers [here]("http://ubuntuforums.org/showthread.php?p=423589") or go to a 32bit kernel. I'm sorry I can't add more helpful advice.

```

horndog@HornDogsHouse:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5582 (8.21.7)

```

```

horndog@HornDogsHouse:~$ glxgears -printfps
22532 frames in 5.0 seconds = 4506.368 FPS
22514 frames in 5.0 seconds = 4502.702 FPS
22548 frames in 5.0 seconds = 4509.424 FPS
22506 frames in 5.0 seconds = 4501.167 FPS
22553 frames in 5.0 seconds = 4510.455 FPS
22558 frames in 5.0 seconds = 4511.472 FPS
21421 frames in 5.0 seconds = 4284.077 FPS

```

---

### Post by preserved on 2006-01-28
Ahh you ran glxgears but i ran fgl_glxgears. 
fgl_glxgears is supposed to be more taxing on the system..

Running glxgears:

preserved@Highspeed:~$ glxgears -printfps
22754 frames in 5.0 seconds = 4550.732 FPS
23233 frames in 5.0 seconds = 4646.503 FPS
35764 frames in 5.0 seconds = 7152.713 FPS
33903 frames in 5.0 seconds = 6780.406 FPS
22719 frames in 5.0 seconds = 4543.790 FPS

---

### Post by Horndog on 2006-01-28
Sorry I was not aware of that one. Some games are dogs in Linux. I have UT2003 and UT2004 that run better in ubuntu than in Windows Then there is Quake4, other than being a total disappointment, it runs like crap in ubuntu Your problem just might be a doggy game for Linux. I hear It was a dog for Windows too. I must say I never tried that game.

```

horndog@HornDogsHouse:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
4718 frames in 5.0 seconds = 943.600 FPS
4690 frames in 5.0 seconds = 938.000 FPS
4731 frames in 5.0 seconds = 946.200 FPS
4700 frames in 5.0 seconds = 940.000 FPS
4707 frames in 5.0 seconds = 941.400 FPS
4731 frames in 5.0 seconds = 946.200 FPS
4702 frames in 5.0 seconds = 940.400 FPS
4724 frames in 5.0 seconds = 944.800 FPS
4705 frames in 5.0 seconds = 941.000 FPS
4733 frames in 5.0 seconds = 946.600 FPS
4739 frames in 5.0 seconds = 947.800 FPS
4713 frames in 5.0 seconds = 942.600 FPS



```

---

### Post by preserved on 2006-01-28
As far as I have read it should be possible to get it to work without any problems, I will atleast try.

Thanks for your feedback though.

By the way do you know if Alpha Centauri is abandonware for linux? If I recall correctly it is it for Windows.

---

### Post by hav0x on 2006-01-28
If it's not a misconfiguration It's an ATI issue for sure ... i've seen people playing NWN on a TNT2, that gets you what on glxgears? 100fps? ;)

---

### Post by preserved on 2006-01-28
Fps in glxgears are posted above..
From 4500 to 7100 fps

---

### Post by leech on 2006-01-28
My question would be, what video options do you have set?  I know full shadows will bring some cards to their knees.  It runs awesomely on my setup, but then again I have a 6800GT.  With a Radeon 9800 it should run pretty smooth though, unless the ATI drivers broke something that Neverwinter uses.

For the record, Quake 4 ran awesome on my Desktop and quite nicely on my lapop too (6800GT and 6600 Go respectively)

Leech

---

### Post by preserved on 2006-01-28
That was my first reaction, to turn the graphics settings to their lowest, but unfortunatly it didn't help.

When I had Windows installed it ran smoothly at the highest settings.

---

### Post by hav0x on 2006-01-28
[QUOTE=preserved]Fps in glxgears are posted above..
From 4500 to 7100 fps[/QUOTE]

I meant the TNT2 ... *bashes you with the humour stick*
My point was since i've seen people playing it on a TNT2 it must be a probem with ati's support for something.

---

### Post by preserved on 2006-01-28
Yeah, noticed it now, sorry, I am kinda tired right now. It must've affected my sense for humor...

I recall actually playing it on a TNT2 long time ago... well not that long time ago...

---

### Post by preserved on 2006-01-29
If anybody has gotten Neverwinter Night to work with ATI and Ubuntu 5.10, the 64-bits version, I would be glad if they could post a message. Just to tell me that it can be done...

---

### Post by preserved on 2006-01-30
I got it to work, the problem was as suggested ATI drivers.

I am running now on the drivers that came with Ubuntu and Neverwinter Nights runs as smoothly as ever!

If I could reconstruct how I did it I would, but when I suceeded in running Neverwinter Nights it was after a long string of installs, uninstalls and reinstalls. In other words a lot of trial and error.

Those who have questions about how I did can PM me and I will try to answer as good as I can.

---

### Post by tenshi-no-shi on 2007-03-05
I run nwn on my modest computer with a ATI Radeon 7500 (Fully supported by open-source drivers). With full graphics I get like 7.5 fps in the game with everything turned down I get around 22 fps. Though strangely at the 7.7 fps it still runs smoothly, I think either the fps output in the game is off or somehow it has frameskipping. Oh well the flgrx drivers are crap from my understanding, and don't support older card, but then ATI drivers are pretty bad for windows too.

---

