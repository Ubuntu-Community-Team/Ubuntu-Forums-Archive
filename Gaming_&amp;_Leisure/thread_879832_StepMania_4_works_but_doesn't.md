---
title: "StepMania 4 works but doesn't"
date: 2008-08-04
forum: Gaming &amp; Leisure
---

### Post by Eman64 on 2008-08-04
Ok, so I've searched the Forums, and while people are having problems with SM, none of them are like mine.

When I go to play the game, everything works fine, but once I select my difficulty, the game just stops there. Everything works fine, it just doesn't go to the song selection screen (I believe that's what's next).

Has anyone had/heard of this problem?

Thanks for your time

---

### Post by SantiSolari on 2008-08-05
I have the SAME problem!! I tried waiting the timer count down to zero but it stays in that screen, In the dificulty selection screen! does anyone knows what to do!!? please!:(

---

### Post by louman on 2008-08-10
I'm experiencing the exact same issue, I'll be sure to post a fix if I manage to figure it out.

I'm using the .deb from getdeb.net:
[http://www.getdeb.net/app/StepMania](http://www.getdeb.net/app/StepMania)

What is everyone else using?

---

### Post by DPic on 2008-09-24
Same problem here! Anybody know if this will be fixed?

---

### Post by badgandalf on 2008-09-28
Exactly the same problems here. Running Kubuntu Hardy and StepMania 4. I also tried SM 3.9 but cannot get it to start. Ignacio

---

### Post by Holonet on 2008-09-28
StepMania 4 isn't released as stable yet, as far as I know, so that could play a part in it...but if 3.9 won't work...  getlibs will take care of the libraries the game needs.  Do that if you haven't.

---

### Post by badgandalf on 2008-09-28
It works! Thx,
Ignacio

---

### Post by badgandalf on 2008-09-28
It doesn't work. Stepmania 3.9 started to work a couple times. Then, when i returned to the PC to try and make it work again it goes to the splash screen and dissapears almost instantly.

Here you are the contects of the log.txt, in case they help give me a hint of what might be going on:

[I]00:00.008: StepMania 3.9
00:00.009: Log starting 2008-09-28 20:18:41
00:00.009:
00:00.009: Reading 'Data/Defaults.ini' failed: No such file or directory
00:00.009: Reading 'Data/StepMania.ini' failed: No such file or directory
00:00.009: Reading 'Data/Static.ini' failed: No such file or directory
00:00.116: Loading window: gtk
00:00.116: OS: Linux ver 020624
00:00.116: Crash backtrace component: x86 custom backtrace
00:00.116: Crash lookup component: dladdr
00:00.116: Crash demangle component: cxa_demangle
00:00.116: Runtime library: glibc 2.7
00:00.116: Threads library: NPTL 2.7
00:00.116: TLS is available
00:00.116: AnnouncerManager::AnnouncerManager()
00:00.116: Reading 'Data/GamePrefs.ini' failed: No such file or directory
00:00.116: Reading 'Data/Static.ini' failed: No such file or directory
00:00.117: ThemeManager::SwitchThemeAndLanguage: "default", ""
00:00.156: Initializing driver: ALSA
00:00.163: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.16.
00:00.163: ALSA Driver: 0: HDA VIA VT82xx [VT82xx], device 0: ALC883 Analog [ALC883 Analog], 0/1 subdevices avail
00:00.164: ALSA Driver: 0: HDA VIA VT82xx [VT82xx], device 1: ALC883 Digital [ALC883 Digital], 1/1 subdevices avail
00:00.164: ALSA error: pcm_hw.c:1099 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)
00:00.165: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy
00:00.165: Initializing driver: ALSA-sw
00:00.165: OS: Linux ver 020624
00:00.165: ALSA error: pcm_hw.c:1099 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)
00:00.165: Mixing 0.000000 ahead in 0 Mix() calls
00:00.166: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy
00:00.166: Initializing driver: OSS
00:00.166: Mixing 0.000000 ahead in 0 Mix() calls
00:00.166: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy
00:00.166:
00:00.166: //////////////////////////////////////////////////////
00:00.166: Exception: Couldn't find a sound driver that works
00:00.166: //////////////////////////////////////////////////////
00:00.166:
00:00.166: Language: english
00:00.166: Theme: default[/I]

Thnx,

Ignacio

---

### Post by badgandalf on 2008-09-28
Found the problem. I needed to close all programs with access to the sound card before trying to start the program. Thnx everybody for the help,

Ignacio

---

### Post by CharonM72 on 2008-10-05
getlibs? Is this a command-line function? It doesn't do anything and apt-get doesn't have it. What am I missing here?

---

### Post by Perfect Storm on 2008-10-05
getlibs is an CLI application that are used for installing 32-libs (in /usr/lib32) on 64-bit, you can find/search it in our 64-bit forum.

---

