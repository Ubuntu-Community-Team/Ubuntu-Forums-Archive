---
title: "sdlmame no sound any recent version of ubuntu"
date: 2009-08-27
forum: Gaming &amp; Leisure
---

### Post by chuckyp on 2009-08-27
I'm trying to get sdlmame working with a bare bones system.
Basically what i've done.

I installed a command line system, then I installed Xorg and nvidia drivers. I have X working and everything else; however, I can not get sound through sdlmame. I've tried various fixes suggested including installing libsdl1.2debian-all libsdl1.2debian-pulseaudio etc... switching back and forth. Nothing is muted at this time and sound works in other applications.

The only way I was able to get sound working in sdlmame at one point was to install the ubuntu-desktop package and all the gnome garbage that I don't want on the cabinet. I then installed libsdl1.2debian-all and it started working.

I would like to get sound working without having gnome and all the extras installed as this machine will be a strictly in a cabinet. I'm at a loss i've tried about everything I can think of and I'm looking for suggestions.

I've tried both versions of SDLmame from the repos and from the web. Both show the same behavior. I've also tried different distros including 8.10 9.04 and 9.10 all show the same behavior witht he package. ON ANY SOUND HARDWARE.  This is a dependancy issue as far as i'm concerned. I just can't figure out what missing dependency is causing it.

---

### Post by chuckyp on 2009-08-27
Okay after some googling and reading bug reports of different sdl sound issues. I believe from my prior experience with libsdl1.2debian-all and having specified SDL_AUDIODRIVER="esd" fixed the issue before. So i'm going to try and install libsdl1.2debian-esd later tonight. See if that will resolve some issues with sdlmame in ubuntu.

---

### Post by chuckyp on 2009-08-27
Okay I'm back at the starting board I still can't figure out whats going on here. I tried installing the esd package with no luck. Looking for any ideas

---

