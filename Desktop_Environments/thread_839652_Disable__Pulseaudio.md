---
title: "Disable  Pulseaudio"
date: 2008-06-24
forum: Desktop Environments
---

### Post by chaosdesigner on 2008-06-24
Hi,

Im using wine and i had a problem with a game so i asked in the wine Forum and i was told to disable oder remove pulseaudio, can i just do that or will this affect other applications?

Well here is my problem:

the instalation worked good but when i try to open the game i get this message:

ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x197a520,0x00000004,0x197a51c) Unknown information class 

I have ubuntu 8.04 and the game is nba 08, 

thx

---

### Post by Vivaldi Gloria on 2008-06-25
Why don't you try to fix pulseaudio following one of the guides:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

I used the second thread to fix all my sound issues but the first thread is newer. Now I can start an OSS application with

```
padsp <some-oss-program>
```

and it plays fine. In particular, i chose OSS in wine and i use this for wine apps.

---

