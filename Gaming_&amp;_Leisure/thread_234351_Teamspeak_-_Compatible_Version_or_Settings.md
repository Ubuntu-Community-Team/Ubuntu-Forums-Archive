---
title: "Teamspeak - Compatible Version or Settings?"
date: 2006-08-11
forum: Gaming &amp; Leisure
---

### Post by Lightmans on 2006-08-11
Hello my friends,
iam a online gamer -> EVE -> I emulate this game with Wine/Cedega. -> Works fine

Now the problem, i would also speak with my friends over Teamspeak and at the same time play EVE, but it is not possible.

Because, everbody now -> Teamspeak2 only uses OSS and is not alsa compatible. :( And i use Dapper 6.06 - Gnome - Alsa - Teamspeak2 and i use the soundserver ALSA

Now, i occupy myself sine one week with this problem and have tried some wikis and howtos.

for example:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound) 
& 
[http://forum.goteamspeak.com/showthread.php?t=9687&highlight=aoss](http://forum.goteamspeak.com/showthread.php?t=9687&highlight=aoss) 

Soo... i have now learned new things and very much with this howtos, but no one of this solves could help me with my problem.
i can not use the to applications together.

I repeat here now my problem:
- i start only cedega 5.2 with EVE and use in the game the soundserver ALSA and user the "default" driver. -> i have sound and can play.

- i start only Teamspeak2 with the default configuration (dev/dsp) -> i have sound and can speak normal with my friends.

BUT: When i use the two applications together, i dont hear the gamesound OR i dont hear and cant speak with Teamspeak.
Only one of them will go...

Now my questions:
1.) Anybody have this constelation running?
(gnome, dapper, eve, cededga, teamspeak2) 
2.) Did anybody now a solution for my problem?
3.) Exist a other Tool that is compatible with Teamspeak and i can use under linux a other clientapplication with Teamspeak server?
4.) Can somebody help me? i cant get that SHI... running togehter? :mrgreen: 

And now here some informations:

```

root@lightmans2:~# uname -r 
2.6.15-26-686 
------------------------------------------------------ 

root@lightmans2:~# lspci | grep audio 
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
------------------------------------------------------ 

root@lightmans2:~# lsmod | grep snd[/color] 
snd_pcm_oss            56448  0 
snd_mixer_oss          20544  1 snd_pcm_oss 
snd_intel8x0           35772  4 
snd_ac97_codec        100224  1 snd_intel8x0 
snd_ac97_bus            2400  1 snd_ac97_codec 
snd_pcm                96708  4 snd_pcm_oss,snd_intel8x0,snd_ac97_codec 
snd_timer              26884  2 snd_pcm 
snd                    60004  12 snd_pcm_oss,snd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer 
soundcore              10784  1 snd 
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm 

------------------------------------------------------ 
root@lightmans2:~# cat /proc/asound/cards 
0 [ICH5           ]: ICH4 - Intel ICH5 
                     Intel ICH5 with ALC655 at 0xfebffa00, irq 209 

------------------------------------------------------ 
root@lightmans2:~# cat /proc/asound/devices 
 20: [0- 4]: digital audio playback 
 27: [0- 3]: digital audio capture 
 26: [0- 2]: digital audio capture 
 25: [0- 1]: digital audio capture 
 16: [0- 0]: digital audio playback 
 24: [0- 0]: digital audio capture 
  0: [0- 0]: ctl 
 33:       : timer 

------------------------------------------------------ 
root@lightmans2:~# cat /proc/asound/pcm 
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1 
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1 
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1 
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1 
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1 

------------------------------------------------------ 
root@lightmans2:~# cat /proc/asound/oss/devices 
  0: [0- 0]: mixer 
  3: [0- 3]: digital audio 
 12: [0-12]: digital audio 

------------------------------------------------------ 
root@lightmans2:~# ls /dev/*dsp* -l 
crw-rw---- 1 root audio 14, 12 2006-08-10 22:01 /dev/adsp 
crw-rw---- 1 root audio 14,  3 2006-08-10 22:01 /dev/dsp 

------------------------------------------------------ 

cat /dev/urandom > /dev/dsp (sound there) 
cat /dev/urandom > /dev/adsp (no sound and i become a error msg) 
-bash: /dev/adsp: No such device 


```



This i have also tried:
sudo -s 
echo "et.x86 0 0 disable">/proc/asound/card0/pcm1c/oss 
echo "quake3.x86 0 0 disable">/proc/asound/card0/pcm1c/oss 

and this too!:

aoss /opt/TeamSpeak2RC2/TeamSpeak.bin "$@" -> Teamspeak will be loaded and started but the speaker and the mic are off and i cant use it. And i become no error message.

It would be nice, if anybody can help me with this problem!!
Thank you and greetings,
Lightmans 

_________________
Let live and let live...

---

