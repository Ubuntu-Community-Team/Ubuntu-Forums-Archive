---
title: "Need help installing stepmania on ubuntu 8.10"
date: 2008-12-27
forum: Gaming &amp; Leisure
---

### Post by MR.UNOWEN on 2008-12-27
Hello, can someone help me with getting step mania to work? 

Everytime I click on "sepmania" it fails to run. 

Here's the log file:  
> 00:00.016: StepMania 3.9

00:00.017: Log starting 2008-12-27 13:03:27

00:00.017:  

00:00.018: Reading 'Data/Defaults.ini' failed: No such file or directory

00:00.018: Reading 'Data/StepMania.ini' failed: No such file or directory

00:00.018: Reading 'Data/Static.ini' failed: No such file or directory

00:00.267: Loading window: gtk

00:00.268: OS: Linux ver 020627

00:00.268: Crash backtrace component: x86 custom backtrace

00:00.268: Crash lookup component: dladdr

00:00.268: Crash demangle component: cxa_demangle

00:00.268: Runtime library: glibc 2.8.90

00:00.268: Threads library: NPTL 2.8.90

00:00.268: TLS is available

00:00.269: AnnouncerManager::AnnouncerManager()

00:00.269: Reading 'Data/GamePrefs.ini' failed: No such file or directory

00:00.269: Reading 'Data/Static.ini' failed: No such file or directory

00:00.271: ThemeManager::SwitchThemeAndLanguage: "default", ""

00:00.383: Initializing driver: ALSA

00:00.409: ALSA: Advanced Linux Sound Architecture Driver Version 1.0.17.

00:00.409: ALSA Driver: 0: HDA Intel [Intel], device 0: ALC269 Analog [ALC269 Analog], 0/1 subdevices avail

00:00.412: ALSA error: pcm_hw.c:1321 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)

00:00.413: Couldn't load driver ALSA: dsnd_pcm_open(hw:0): Device or resource busy

00:00.413: Initializing driver: ALSA-sw

00:00.414: OS: Linux ver 020627

00:00.415: ALSA error: pcm_hw.c:1321 snd_pcm_hw_open: open /dev/snd/pcmC0D0p failed (Device or resource busy)

00:00.415: Mixing 0.000000 ahead in 0 Mix() calls

00:00.415: Couldn't load driver ALSA-sw: dsnd_pcm_open(hw:0): Device or resource busy

00:00.415: Initializing driver: OSS

00:00.416: Mixing 0.000000 ahead in 0 Mix() calls

00:00.416: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy

00:00.416: 

00:00.416: //////////////////////////////////////////////////////

00:00.416: Exception: Couldn't find a sound driver that works

00:00.416: //////////////////////////////////////////////////////

00:00.416: 

00:00.416: Language: english

00:00.417: Theme: default


---

### Post by Vadi on 2008-12-27
Where you install it from?

---

### Post by MR.UNOWEN on 2008-12-27
I just extracted the compressed file to the desktop and tried running it.

---

### Post by Vadi on 2008-12-27
> 00:00.416: Couldn't load driver OSS: RageSound_OSS: Couldn't open /dev/dsp: Device or resource busy

I... think it doesn't work if you have something else using sound. Not sure why is that so.

---

### Post by MR.UNOWEN on 2008-12-29
> **Vadi said:**
> I... think it doesn't work if you have something else using sound. Not sure why is that so.

Ya... that was the problem.... Even just having firefox up will cause it not to work....  

How can I resolve this problem???   It's kind  of annoying having to close all applications just to play that game.

---

### Post by cocodude on 2008-12-30
Although I haven't seen this problem before, have you tried running stepmania prefixed by 'padsp' to put a wrapper around OSS (/dev/dsp) to try and use PulseAudio (the sound server in 8.10?

Try running 'padsp stepmania' in the appropriate directory.

---

### Post by MR.UNOWEN on 2008-12-31
> **cocodude said:**
> Although I haven't seen this problem before, have you tried running stepmania prefixed by 'padsp' to put a wrapper around OSS (/dev/dsp) to try and use PulseAudio (the sound server in 8.10?

Try running 'padsp stepmania' in the appropriate directory.

What's "padsp"???? I'm not sure what to do...  could you explain that in a way any dead brain person could understand...

---

