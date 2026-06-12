---
title: "Diablo 2 Sound Problems"
date: 2006-02-18
forum: Gaming &amp; Leisure
---

### Post by deboring21 on 2006-02-18
Well, I installed Wine during the following of this HowTo: [http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)
When I do Winecfg, I can't edit the sound options, I get this error message:

ALSA lib seq_hw.c:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/ryan/.kde/socket-Cerebro.
can't create mcop directory

....and get booted out of Winecfg.... Now I followed this HowTo: [http://ubuntuforums.org/showthread.php?t=99154&highlight=diablo+II](http://ubuntuforums.org/showthread.php?t=99154&highlight=diablo+II)
When I start up Diablo 2, I don't get any sound.... What should I do?
-Ryan

---

### Post by noObiE_4_life on 2006-02-19
[QUOTE=deboring21]Well, I installed Wine during the following of this HowTo: [http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)
When I do Winecfg, I can't edit the sound options, I get this error message:

ALSA lib seq_hw.c:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/ryan/.kde/socket-Cerebro.
can't create mcop directory

....and get booted out of Winecfg.... Now I followed this HowTo: [http://ubuntuforums.org/showthread.php?t=99154&highlight=diablo+II](http://ubuntuforums.org/showthread.php?t=99154&highlight=diablo+II)
When I start up Diablo 2, I don't get any sound.... What should I do?
-Ryan[/QUOTE]

Do you have any other programs working with wine? I'm guessing not. Try making the directory that it's calling for,  /home/ryan/.kde/socket-Cerebro 
I suppose its just a permissions issue on your machine. You'll notice its your home directory and machine name, btw. 

Afterward, run winecfg. I found that the ESD sound would produce bad pauses . I switched to ALSA and all worked fine.

---

### Post by ed_d on 2006-02-21
He has WoW working with sound fine. When you run winecfg, and try to even go to the sound tab, winecfg closes. I am wondering if it has to do with the patch that was installed with the link he provided.

---

### Post by jalonsom on 2006-03-19
I have the same problem with the audio tab in winecfg.
I have wine 0.99 in Dapper.
No winetools, just wine, ies4linux and foobar installed. Sound doesn't work.
Any idea? Any solution?

---

### Post by LordMelkor on 2006-03-19
create the directory that it cant find, then usually it works fine, also uncheck everything but OSS, as OSS has the best compatability.

---

### Post by jalonsom on 2006-03-20
There's another possible workaround that I found in the corresponding wine [bug report]("http://bugs.winehq.org/show_bug.cgi?id=4051"):

Just rename /usr/lib/wine/winearts.drv.so to something else so that wine does not find it. It worked for me although sound is still a bit buggy (ALSA with hardware acceleration works with strange sound the first time a sound is played, without acceleration works fine, other drivers don't work properly: ESD sound is choppy and others simply don't work).

It is quite dirty and results are impredictable, so I would try first creating the directory as suggested.

---

