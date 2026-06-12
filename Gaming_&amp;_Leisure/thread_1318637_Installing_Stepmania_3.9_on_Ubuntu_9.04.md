---
title: "Installing Stepmania 3.9 on Ubuntu 9.04"
date: 2009-11-07
forum: Gaming &amp; Leisure
---

### Post by WutCake on 2009-11-07
Hello everyone, I've been googling and searching a few hours now.

since it appears to be that all the other tutorials or howto's is old and does not work like that any more because of the files changed in the archives.

what i can tell you, is that i downloaded both the binary and source code, unable to install either of them.

i double clicked the files, nothing happens, except i think some files gets removed or added, can't tell really.  


thanks in advise.

---

### Post by WutCake on 2009-11-16
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar:

---

### Post by beastrace91 on 2009-11-16
I'd also be interested in getting this working, I tried awhile back but was less than successful. Their source code throws piles of errors when trying to compile and the binary they provide fails to install properly as well :/

~Jeff

---

### Post by hikaricore on 2009-11-16
You can always try the old packages on GetDeb.net: [http://old.getdeb.net/app/StepMania](http://old.getdeb.net/app/StepMania)
They've worked fine for me since hardy.

---

### Post by fromthehill on 2009-11-17
download the linux binary (a tar.gz) file
put the folder thats in the package somewhere (I put it in my home folder)
dubblecklick on the executable(caled stepmania) in the folder
the game should start

if it doesn't start close firefox(and any other program that has used sound or video) and try again

---

### Post by beastrace91 on 2009-11-17
Thanks for the tips - I'll have to give that .deb file a try when I get home. If it works then it is time to get out my dance pads I think... :)

~Jeff

---

### Post by WutCake on 2009-11-28
[html]
00:00.015: StepMania 3.9 
00:00.015: Log starting 2009-11-28 17:47:21 
00:00.015:   
00:00.015: Reading 'Data/Defaults.ini' failed: No such file or directory 
00:00.016: Reading 'Data/StepMania.ini' failed: No such file or directory 
00:00.016: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.292: Loading window: gtk 
00:00.292: OS: Linux ver 020628 
00:00.292: Crash backtrace component: x86 custom backtrace 
00:00.292: Crash lookup component: dladdr 
00:00.292: Crash demangle component: cxa_demangle 
00:00.293: Runtime library: glibc 2.9 
00:00.293: Threads library: NPTL 2.9 
00:00.293: TLS is available 
00:00.293: AnnouncerManager::AnnouncerManager() 
00:00.293: Reading 'Data/GamePrefs.ini' failed: No such file or directory 
00:00.293: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.295: ThemeManager::SwitchThemeAndLanguage: "default", "" 
00:00.415: Initializing driver: ALSA 
00:00.443: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.18rc3. 
00:00.443: ALSA Driver: 0: HDA NVidia [NVidia], device 0: CONEXANT Analog [CONEXANT Analog], 0/1 subdevices avail 
00:00.444: ALSA Driver: 0: HDA NVidia [NVidia], device 1: Conexant Digital [Conexant Digital], 1/1 subdevices avail 
00:00.451: ALSA error: pcm_hw.c:1321 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy) 
00:00.452: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.452: Initializing driver: ALSA-sw 
00:00.453: OS: Linux ver 020628 
00:00.458: ALSA error: pcm_hw.c:1321 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy) 
00:00.459: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.459: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.459: Initializing driver: OSS 
00:00.460: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.460: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy 
00:00.460:  
00:00.460: ////////////////////////////////////////////////////// 
00:00.460: Exception: Couldn't find a sound driver that works 
00:00.460: ////////////////////////////////////////////////////// 
00:00.460:  
00:00.460: Language: english 
00:00.460: Theme: default 
[/html]

lol.
what if i want firefox open? :(

---

### Post by hypatia on 2010-01-19
Hey Jeff,

In case you didn't get this working on 9.04, I highly recommend installing the latest version from SVN.  There's a nice tutorial here: [http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux](http://www.stepmania.com/wiki/Build_the_StepMania_Source_in_Linux) and it even worked for me in 9.10 Karmic on x64 / AMD64 with pulseaudio, right from the start.  Plus, 4Alpha is so much awesomer than 3.9.

Hope that helps!

---

### Post by AllRadioisDead on 2010-01-19
[http://www.flashflashrevolution.com/](http://www.flashflashrevolution.com/)
Why not just play flash flash?

---

