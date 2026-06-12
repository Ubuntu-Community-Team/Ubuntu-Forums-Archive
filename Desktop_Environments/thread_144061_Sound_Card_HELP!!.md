---
title: "Sound Card HELP!!"
date: 2006-03-13
forum: Desktop Environments
---

### Post by seismicmike on 2006-03-13
My sound card does not like me. I have sound that I can hear, but the volume is WAY quiet!! I don't know how to fix it!! HELP!!

lspci | grep audio:

```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```

lsmod | grep sound:

```
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  7 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
```

I don't know what most of this means, but I figure it would help. Thank you

---

### Post by mustang on 2006-03-13
Did you try

```
alsamixer
```

and messing around with sliders--particularly the master and PCM ones?

---

### Post by seismicmike on 2006-03-13
[QUOTE=mustang]Did you try

```
alsamixer
```

and messing around with sliders--particularly the master and PCM ones?[/QUOTE]

yeah, they're all up full blast... :-k 

thanks for the suggestion

---

### Post by bobpur on 2006-03-13
Have you checked for proper drivers. A different driver may help. Also, If you have "onboard" audio, Get into your BIOS and change from "enable" to "disable."

---

### Post by bobpur on 2006-03-13
In my limited knowledge, the reference to "ac_97 codec" leads me to believe you have a conflict between on board audio and your sound card. I just saw that. Disable on board sound.

---

### Post by seismicmike on 2006-03-13
[QUOTE=bobpur]In my limited knowledge, the reference to "ac_97 codec" leads me to believe you have a conflict between on board audio and your sound card. I just saw that. Disable on board sound.[/QUOTE]

will that cause problems when I'm in windows? I'm dual booting

---

### Post by bobpur on 2006-03-14
No, it shouldn't. 
When you're in Windows, you'll be using the drivers that came on your installation CD  for your sound card. When you're in Ubuntu, you'll be using whatever driver Ubuntu has for your soundcard. 
Two different OS's and two different drivers.
If you've got "On (mother) Board Audio, as I suspect, disabling it should give you a noticeable boost in audio performance no matter which OS you're running.
Good Luck!



"If it ain't broke, fix it 'til it is and then re-install!"

---

### Post by seismicmike on 2006-03-14
Alright. I'll try that. Thanks!

---

### Post by seismicmike on 2006-03-14
Well... I got a couple of issues.

1. I couldn't find in my BIOS settings where I could disable onboard sound

2. I'm on my laptop, and the only sound card I have is the one built in, which I think is onboard, so I think I want to have the onboard sound enabled... but I don't know for sure.

I don't know if that makes any difference

Thanks for your help

---

### Post by bobpur on 2006-03-14
OK then, I thought we were talking about two different creatures here. On board audio and an actual PCI slot type soundcard. I didn't see any thing about a laptop until just now on your last post. Yeah, if that's all you got then you really should have that enabled. Well, check your driver or try another one. Sorry 'bout that.

---

### Post by Peter41az on 2006-03-14
i have ac97.. I had same problem, I had to turn up the equalizer settings in various programs like mplayer to even hear it.. try running mplayer, then turn up the sliders in EQ, (especially the middle ones) and see if the sound gets louder.

---

### Post by seismicmike on 2006-03-15
[quote=bobpur]OK then, I thought we were talking about two different creatures here. On board audio and an actual PCI slot type soundcard. I didn't see any thing about a laptop until just now on your last post. Yeah, if that's all you got then you really should have that enabled. Well, check your driver or try another one. Sorry 'bout that.[/quote]

Ah, you're fine. Thanks for the help. :). I'll keep banging away at it!

](*,)

---

