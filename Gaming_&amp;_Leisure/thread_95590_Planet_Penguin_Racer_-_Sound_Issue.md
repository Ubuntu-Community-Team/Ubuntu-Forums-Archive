---
title: "Planet Penguin Racer - Sound Issue"
date: 2005-11-26
forum: Gaming &amp; Leisure
---

### Post by musther on 2005-11-26
I have no sound in planet penguin racer, not sure why.   According to the multimedia systems selector I am using ALSA, but ESD also works.

Cheers

---

### Post by manicka on 2005-11-27
Try 'killall esd' before running penguin racer

---

### Post by ropers on 2007-09-28
I also have no sound. I'm not sure what musther is referring to when s/he speaks of the "multimedia systems selector", but when I try to open ppracer from the command line I get this: 

[INDENT]```
$ ppracer
PPRacer 0.3.1 --  http://racer.planetpenguin.de 
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
PPRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

ALSA lib pcm_dmix.c:914:(snd_pcm_dmix_open) unable to open slave
%%% ppracer warning: Warning: Couldn't set 11025 Hz 8-bit audio
  Reason: No available audio device


```[/INDENT]

What do I need to do now?

---

