---
title: "Radeon 7000REX, Choppy video? (VLC,YOUTUBE ETC ETC)"
date: 2006-08-11
forum: Desktop Environments
---

### Post by orasis on 2006-08-11
Hello, I have noticed that no matter what I have choppy video under Ubuntu using my Radeon 7000 card, perhaps someone knows of a fix - it seems that my card is running in software mode when it plays these videos.. maybe there is a way to set it to hardware? or someone has had the same experiences and has found a better driver?

Keep in mind, my desktop experience is pretty much perfect no real slow down for flash ads, or animated web stuff - but when it comes to sites like Youtube, and Mpegs (unless they are like small ones) just chug a long.

It is watchable, but you can notice the chop and it gets on my nerves after a while. - And I am sure it is a software rendering issue since, if I have a bit torrent download running then the video gets REALLY choppy. 

I am running a PIII 1GHZ 256MEGS RAM, more then enough power to run videos smoothly, but anyways please let me know if you have had this happen to you before - and how did you solve it? :-k 

Thanks in advance. - Orasis.

---

### Post by kaamos on 2006-08-11
Hello!

Have you tried different video outputs? In vlc this setting can be found under preferences (check "show advanced") -> video -> output modules. Also, are you using the closed source fglrx driver or oss ati/radeon?

---

### Post by orasis on 2006-08-11
> **kaamos said:**
> Hello!

Have you tried different video outputs? In vlc this setting can be found under preferences (check "show advanced") -> video -> output modules. Also, are you using the closed source fglrx driver or oss ati/radeon?

Hi, thanks for the response. 

I have tryed all outputs in the advanced VLC settings from the default to the OpenGL. - As for the driver, I am using the driver that came stock with Ubuntu I have not switched since I installed. 

Which one do you recommend?

(Oh and again, just want to make it clear - the video is only choppy when watching movies or youtube or google video etc, all other desktop activities are nice and smooth.)

---

### Post by Ramses de Norre on 2006-08-11
For a better (non-open source) driver: ```
sudo aptitude install xorg-driver-fglrx
```
Then do ```
sudo gedit /etc/X11/xorg.conf
```
Search the Device section for your video card and change the value after Driver to fglrx, press ctrl-alt-backspace to restart X.

---

### Post by orasis on 2006-08-11
> **Ramses de Norre said:**
> For a better (non-open source) driver: ```
sudo aptitude install xorg-driver-fglrx
```
Then do ```
sudo gedit /etc/X11/xorg.conf
```
Search the Device section for your video card and change the value after Driver to fglrx, press ctrl-alt-backspace to restart X.

Sounds good, hope it does not break my system - it is so pretty at the moment, thank you very much - and I will respond to the forum as to what happens.

---

### Post by Ramses de Norre on 2006-08-11
You can just change the driver back to the old one if he doesn't work good ;)

---

### Post by orasis on 2006-08-11
That is interesting, I do not know if it is supposed to be like that but my Radeon is an AGP card, and in the Device section it says something to the effect of PCI:1:0:0 

Is that normal?

---

### Post by orasis on 2006-08-11
Nope does not work, starts a few times - and then leaves me an error log, I read the error log, the device driver was released in 2006 and out of all chipsets it supports Radeon 7000 is not one of them. 

So Flgrfx (from memory) does not support or work with the Radeon 7000.

---

### Post by orasis on 2006-08-11
Is anyone familiar with the DRI project, has anyone used that before?

---

### Post by orasis on 2006-08-11
Well, even though it did not fix my problem.. somehow re-editing my conf back to ATI has made my terminal fonts change.. they are nicer now.. go figure :-k  lol..

---

### Post by kaamos on 2006-08-11
If you have not tried that yet, change the driver to "radeon".

(You might have to execute the command "sudo modprobe radeon" as well)

FYI:
In my opinion the radeon driver is actually much better than fglrx. More stable, no weird bugs in TC:Elite of Nexuiz, zsnes can use OpenGL, Xgl/Compiz actually work (a mobility card). The downside is that is not that fast as fglrx in FPS games. But radeon still runs those just fine in 1024x768 resolution with fairly good graphics.

So if you get radeon going, don't worry about fglrx not being supported. :)

---

### Post by orasis on 2006-08-11
I will try that, BUT - I have found the culprit of the choppy VLC video (Mpeg's and such) - The SETI@HOME client was sucking all of my CPU time (87%)..
So yeah.. I probably will not install that again any time soon :) 

However did not change anything for Youtube or Google.. - but at least my real video problem is fixed. 

ps -e -o pcpu,cpu,nice,state,cputime,args --sort pcpu | sed '/^ 0.0 /d' 

^^^
For your cpu usage by process if ever you feel like your video is getting choppy ;)

---

