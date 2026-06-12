---
title: "Stepmania in Ubuntu"
date: 2010-08-05
forum: Gaming &amp; Leisure
---

### Post by Insertion_Epsilon on 2010-08-05
Hi, I've downloaded Stepmania 3.9a for Linux and it doesn't run when I double-click the extension. I'm guessing a sound driver problem because the log says so. For your information I've copied the whole log here:
```
00:00.003: StepMania 3.9 
00:00.003: Log starting 2010-08-05 22:54:15 
00:00.003:   
00:00.003: Reading 'Data/Defaults.ini' failed: No such file or directory 
00:00.003: Reading 'Data/StepMania.ini' failed: No such file or directory 
00:00.003: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.063: Loading window: gtk 
00:00.063: OS: Linux ver 020632 
00:00.063: Crash backtrace component: x86 custom backtrace 
00:00.063: Crash lookup component: dladdr 
00:00.063: Crash demangle component: cxa_demangle 
00:00.063: Runtime library: glibc 2.11.1 
00:00.063: Threads library: NPTL 2.11.1 
00:00.063: TLS is available 
00:00.063: AnnouncerManager::AnnouncerManager() 
00:00.063: Reading 'Data/GamePrefs.ini' failed: No such file or directory 
00:00.064: Reading 'Data/Static.ini' failed: No such file or directory 
00:00.064: ThemeManager::SwitchThemeAndLanguage: "default", "" 
00:00.087: Initializing driver: ALSA 
00:00.127: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.21. 
00:00.127: ALSA Driver: 0: HDA Intel [Intel], device 0: AD198x Analog [AD198x Analog], 0/1 subdevices avail 
00:00.127: ALSA Driver: 0: HDA Intel [Intel], device 3: INTEL HDMI [INTEL HDMI], 1/1 subdevices avail 
00:00.128: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy) 
00:00.128: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.128: Initializing driver: ALSA-sw 
00:00.128: OS: Linux ver 020632 
00:00.128: ALSA error: pcm_hw.c:1293 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy) 
00:00.128: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.128: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy 
00:00.128: Initializing driver: OSS 
00:00.128: Mixing 0.000000 ahead in 0 Mix() calls 
00:00.128: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy 
00:00.128:  
00:00.128: ////////////////////////////////////////////////////// 
00:00.128: Exception: Couldn't find a sound driver that works 
00:00.128: ////////////////////////////////////////////////////// 
00:00.128:  
00:00.129: Language: english 
00:00.129: Theme: default
```

So, what should I do to solve this problem?

---

