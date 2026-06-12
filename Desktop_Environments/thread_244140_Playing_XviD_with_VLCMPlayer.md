---
title: "Playing XviD with VLC/MPlayer"
date: 2006-08-26
forum: Desktop Environments
---

### Post by srunni on 2006-08-26
Hey, I've been trying to play XviD encoded .avi files in VLC and MPlayer, but all I get is the sound, with a blank screen. Does anyone know how I can fix this?

---

### Post by srunni on 2006-08-26
Any ideas?

---

### Post by srunni on 2006-08-27
Anyone there?

---

### Post by taurus on 2006-08-27
Have you installed all the codecs on your machine?

---

### Post by dentaku65 on 2006-08-27
see:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by srunni on 2006-08-27
> **taurus said:**
> Have you installed all the codecs on your machine?

I've installed the "w32codecs" package, if that's what you mean.

---

### Post by srunni on 2006-08-27
> **dentaku65 said:**
> see:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I installed everything for Kubuntu 6.06 under the "How to Make Things Work in a Hurry", and it still doesn't work with MPlayer, Kaffeine, or VLC. Is it possible that this is due to something wrong with my graphics card configuration?

---

### Post by dentaku65 on 2006-08-27
> **srunni said:**
> I installed everything for Kubuntu 6.06 under the "How to Make Things Work in a Hurry", and it still doesn't work with MPlayer, Kaffeine, or VLC. Is it possible that this is due to something wrong with my graphics card configuration?

do you have xgl/aiglx compiz installed?

---

### Post by srunni on 2006-08-27
No, just the fglrx package. I was going to install xgl, but didn't since I'm running Kubuntu and have and ATI card, when most of the tutorials are for Ubuntu/NVIDIA users. But this was a problem even before I installed fglrx.

---

### Post by srunni on 2006-08-31
Any ideas? I still haven't solved this problem.

---

### Post by srunni on 2006-09-02
I finally managed to fix it, with some help from this thread: [http://www.ubuntuforums.org/showthread.php?t=40273](http://www.ubuntuforums.org/showthread.php?t=40273)
In Kaffeine, I switched the video driver to "xshm" and it works. In MPlayer, I switched it to "X11." Going to try fixing VLC now.
EDIT: There is one bug with X11 in MPlayer: you can't change the video size. For example, if you make the video fullscreen, it will only take up the amount of space it did originally, and leave the rest of the space black.
EDIT #2: In VLC, you change the output module to X11, and it works just fine. Interestingly, using X11 in VLC allows you to go actual fullscreen.

---

### Post by rookie1_1998 on 2006-09-11
I was having the same problem.  This resolved it Thanks.

---

### Post by cian42 on 2006-10-29
How can you change the output module in VLC, i can;t seem ti figure it out?...the solution works in kaffeine an Mplayer.

---

### Post by srunni on 2006-10-29
Settings -> Preferences -> Video -> Output Modules

---

### Post by KDE-fan on 2006-11-06
Thanks, this really solved my problem. All I had to do was install VLC.

---

### Post by srunni on 2006-11-06
Yeah, but Kaffeine works pretty well too ;)

---

### Post by danieldobs on 2006-11-14
> **srunni said:**
> Settings -> Preferences -> Video -> Output Modules

guys, i am not seeing this!? x11 does work with mplayer and i'd love to get vlc up and running .. i can't see anything as such in pref/vid/output .. only snapshot crap .. even on advanced options?

---

### Post by reyfer on 2006-11-14
> **danieldobs said:**
> guys, i am not seeing this!? x11 does work with mplayer and i'd love to get vlc up and running .. i can't see anything as such in pref/vid/output .. only snapshot crap .. even on advanced options?

Maybe this screenshot can help you

---

### Post by srunni on 2006-11-14
You currently have the "Audio" section selected. You need to click on "Output modules."

---

### Post by rafalr on 2007-02-01
Hi, 

had the same problem (dapper on PC and edgy on laptop)

the solution that worked on both was to install "xine-ui" with all codecs and dependencies it was asking for

then things that VLC/Mplayer did not want to play would easily go from xine.

cheers,
Rafal

---

### Post by srunni on 2007-02-03
rafalr:
Your solution is basically the same as mine, the only difference being that you also used the xine frontend. I think the "X11" backend I selected IS the xine engine, meaning that the problem is with the backend, and either method fixes the issue.

---

### Post by thephilS on 2007-02-19
I am having the same problem with Ubuntu Edgy x64. I noticed the problem when trying to play movies ripped by mythtv .20. At first I thought it was a myth problem, but mplayer crashes too and locks up the X server. At least with the mythtv "Internal" player I get the sound and that nice solid blue screen.

installed on the system

xvidcore-1.1.2
ivtv-0.7.3
ffmpeg
a52dec-0.7.4
fame-0.9.0
libfame-0.9.1

I don't know what I'm missing... Some xvid movies do play .... The ones that don't play on the edgy system do play on windows .... I don't know how to check the avi for corruption but you would think it is ok if windows media player can play the file. Any advice would be helpful.

Thanks,

---

### Post by srunni on 2007-02-21
Have you tried using Kaffeine? Sometimes it can play stuff better than mplayer (even though I think they use the same backend).

---

