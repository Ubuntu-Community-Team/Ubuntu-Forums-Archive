---
title: "XMMS doesn't work"
date: 2005-05-16
forum: Desktop Environments
---

### Post by DaGGer on 2005-05-16
ok well i want to be able to listent to music and well i can't....i open up a mp3 file and it doesn't do anything...i have it set on ALSA and it doesn't work still...it might be because of my sound card but i don't have steam or team speak running...so i do'nt get it...can anyone help...is there any other program i need or is it just my sound card..i'm getting a new one but i hav'nt yet gotten it...please help me

---

### Post by lorap on 2005-05-16
hi friend!
one important thing...
XMMS doesn't need any additional codecs been installed, it renders any kinds of files including MP3 very well.
you probably have your sound either disabled or it's just a hardware problem that should be fixed.
check please if your sound card was detected and let anyone who'll try to help you solve this difficulty know that.
p.s.:
to play MP4 files in XMMS additional codecs've be installed.

---

### Post by Staesys on 2005-05-16
Try also changing XMMS to use OSS instead of ALSA and see if it works then.

---

### Post by DaGGer on 2005-05-16
well i have everything set to ALSA because then my counter strike and team speak work...if i don't then they don't work...but it didn't work i don't think even when i had things set to OSS....should i disable all the other sound things such as OSS and what not and see if that helps or what

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=DaGGer]well i have everything set to ALSA because then my counter strike and team speak work...if i don't then they don't work...but it didn't work i don't think even when i had things set to OSS....should i disable all the other sound things such as OSS and what not and see if that helps or what[/QUOTE]

XMMS has an ALSA output plugin that you might have to install as a separate package; this was the case in Gentoo. I'd recommend opening a terminal and doing **apt-cache search xmms | less**. Also, have you tried Beep Media Player? It works similarly to XMMS and uses XMMS skins, and I think it uses ALSA by default.

---

### Post by fng on 2005-05-16
Beep Media Player can also use the winamp 2.x skins
I'm using fryamp right now

---

### Post by DaGGer on 2005-05-16
[QUOTE=fng]Beep Media Player can also use the winamp 2.x skins
I'm using fryamp right now[/QUOTE]
 ok well were do i get beep media player...also when looking through the web i see that i have to have windows media player...anyway i can get this to work with llinux or no

---

### Post by DaGGer on 2005-05-16
i did the apt-cache search command and this is what i got

libflac6 - Free Lossless Audio Codec - runtime C library
libsmpeg0 - SDL MPEG Player Library - shared libraries
amarok - versatile and easy to use audio player for KDE
flac - Free Lossless Audio Codec - command line tools
kopete - Instant messenger program
libflac++-dev - Free Lossless Audio Codec - C++ development library
libflac++4 - Free Lossless Audio Codec - C++ runtime library
libflac-dev - Free Lossless Audio Codec - C development library
libmodplug-dev - ModPlug mod-like music development files
libmodplug0 - ModPlug mod-like music shared libraries
liboggflac++-dev - Free Lossless Audio Codec - C++ development library (ogg)
liboggflac++0c102 - Free Lossless Audio Codec - C++ runtime library (ogg)
liboggflac-dev - Free Lossless Audio Codec - C development library (ogg)
liboggflac1 - Free Lossless Audio Codec - runtime C library (ogg)
vorbisgain - Add suggested volume level for .ogg files as .ogg comment
xmms - Versatile X audio player that looks like Winamp
xmms-dev - XMMS development static library and header files

---

### Post by fng on 2005-05-17
Did you enable the universe repositories?
its in there :

```
fng@butters:~$ apt-cache search beep-media-player
beep-media-player - Versatile audio player that supports Winamp skins
fng@butters:~$
```

---

### Post by pappo on 2005-05-17
Press ctrl-p over xmms and check the "output plugin" settings. If it is set to something different to OSS or Alsa you may be getting the sound sent to some odd place instead of the speakers.

---

### Post by DaGGer on 2005-05-17
no i have it set to ASLA....how do i enable universal thing

---

### Post by ComPro on 2005-05-17
I have to have my sound set to the eSound Output Plugin otherwise XMMS will lock up on me.

Just go into the Options-->Preferences and set it. 8)

---

### Post by fng on 2005-05-18
To enable universe : 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

You dont need to add those last 3 lines in step 4. They are optional for installing beep-media-player.

A lot of usefull tools/tips can be found by folowing that guide,

---

