---
title: "doom3 no sound, doom3-demo has sound"
date: 2007-07-11
forum: Gaming &amp; Leisure
---

### Post by Hoaxe on 2007-07-11
Ok, so here's my problem.

recently i downloaded the doom3 demo of the id site. Great, had loads of fun. sound worked without a hitch, i didn't even know people were having problems because i wasn't! it was even running surround sound.

so i got doom3, installed it, it runs great except that i have no sound. no sound at all, but when i switch back to run doom3-demo, it runs great, surround and everything!! 

i switched my device to OSS but it didn't work. i also tried switching from surround to speaker. still nothing at all. not even shitty 8-bit sound like i read others were having.

so how come the doom3-demo runs without a hitch and the doom3 full app runs without sound?

i have an Audigy 2 Value (SB0400) running on the ALSA mixer.
again, i tried running it in OSS Mixer.

The sound works with everything else, ALSA and OSS, both work, it's only the full game that is not doing the zombie noises.

any tips for my problem?

---

### Post by Hoaxe on 2007-07-12
i get these warning when i run the game, maybe that will help? 

--------------------------------------
-------- Initializing Session --------
WARNING: Couldn't load sound 'guisounds_idlogo.wav' using default
WARNING: Couldn't load sound 'guisounds_chirpconnect.wav' using default
WARNING: Couldn't load sound 'guisounds_menuclickup.wav' using default
WARNING: Couldn't load sound 'guisounds_menuclickdown.wav' using default
WARNING: Couldn't load sound 'guisounds_error.wav' using default
WARNING: Couldn't load sound 'guisounds_click3.wav' using default
WARNING: Couldn't load sound 'guisounds_disconnect1.wav' using default
WARNING: Couldn't load sound 'guisounds_menuerror.wav' using default
WARNING: Couldn't load sound 'guisounds_ping.wav' using default
WARNING: Couldn't load sound 'guisounds_ping2.wav' using default
WARNING: Couldn't load sound 'guisounds_introsound.wav' using default
WARNING: Couldn't load sound 'guisounds_introvo.wav' using default
session initialized
--------------------------------------
Opening IP socket: localhost:-1
--- Common Initialization Complete ---
------------- Warnings ---------------
during DOOM 3 initialization...
WARNING: Couldn't load sound 'guisounds_chirpconnect.wav' using default
WARNING: Couldn't load sound 'guisounds_click3.wav' using default
WARNING: Couldn't load sound 'guisounds_disconnect1.wav' using default
WARNING: Couldn't load sound 'guisounds_error.wav' using default
WARNING: Couldn't load sound 'guisounds_idlogo.wav' using default
WARNING: Couldn't load sound 'guisounds_introsound.wav' using default
WARNING: Couldn't load sound 'guisounds_introvo.wav' using default
WARNING: Couldn't load sound 'guisounds_menuclickdown.wav' using default
WARNING: Couldn't load sound 'guisounds_menuclickup.wav' using default
WARNING: Couldn't load sound 'guisounds_menuerror.wav' using default
WARNING: Couldn't load sound 'guisounds_ping.wav' using default
WARNING: Couldn't load sound 'guisounds_ping2.wav' using default
12 warnings

---

### Post by FoolsGold_MKII on 2007-07-12
Seems like there's a failure to load the sounds in one of the PAK files. Double check to make sure you have all the necessary PAK files copied - perhaps run an md5sum against all the PAK files to see if they match up to the sums listed here (taken from the D3 FAQ):

71b8d37b2444d3d86a36fd61783844fe  base/pak000.pk4
4bc4f3ba04ec2b4f4837be40e840a3c1  base/pak001.pk4
fa84069e9642ad9aa4b49624150cc345  base/pak002.pk4
f22d8464997924e4913e467e7d62d5fe  base/pak003.pk4
38561a3c73f93f2e6fd31abf1d4e9102  base/pak004.pk4

---

### Post by Hoaxe on 2007-07-12
there seems to be in fact a problem with the 003 pack. even copying places from the cd creates errors, i will find another source for the file, thanks.

---

### Post by UK-Wobbie on 2007-07-13
> **Hoaxe said:**
> Ok, so here's my problem.

recently i downloaded the doom3 demo of the id site. Great, had loads of fun. sound worked without a hitch, i didn't even know people were having problems because i wasn't! it was even running surround sound.

so i got doom3, installed it, it runs great except that i have no sound. no sound at all, but when i switch back to run doom3-demo, it runs great, surround and everything!! 

i switched my device to OSS but it didn't work. i also tried switching from surround to speaker. still nothing at all. not even shitty 8-bit sound like i read others were having.

so how come the doom3-demo runs without a hitch and the doom3 full app runs without sound?

i have an Audigy 2 Value (SB0400) running on the ALSA mixer.
again, i tried running it in OSS Mixer.

The sound works with everything else, ALSA and OSS, both work, it's only the full game that is not doing the zombie noises.

any tips for my problem?

Hey call me old :lolflag: I did not no doom 3 will work on ubuntu! What have you got it working on? WINE?
I am going to give it a go :)

---

### Post by PriceChild on 2007-07-13
> **UK-Wobbie said:**
> Hey call me old :lolflag: I did not no doom 3 will work on ubuntu! What have you got it working on? WINE?
I am going to give it a go :)
zerowing.idsoftware.com

---

