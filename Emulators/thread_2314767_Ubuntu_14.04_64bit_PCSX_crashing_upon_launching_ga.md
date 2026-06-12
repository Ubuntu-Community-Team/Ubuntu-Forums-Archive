---
title: "Ubuntu 14.04 64bit PCSX crashing upon launching games"
date: 2016-02-23
forum: Emulators
---

### Post by hook_ham on 2016-02-23
Hi everyone,

This is my first post on this forum and I am relatively new to Ubuntu. I installed it the other week and am trying to get PCSX to run so that I can play the old classics on my laptop.

I don't really know how to output any errors from the terminal but whenever I load PCSX and then select a bin file to run it thinks for a second or two and then just crashes. I almost 100% sure that I have all of the BIOS in the right folder etc but I have no idea how to fix this. I have tried it with lots of different games but none of them seem to work :(

Any help that can guide me towards a solutions would be greatly appreciated. Cheers

---

### Post by potato5 on 2016-02-23
Perhaps you have a graphics card Intel, if so, then:

In Configuration -> Plugins and bios -> Graphics -> select "OpenGL Driver

---

### Post by deadflowr on 2016-02-24
Moved to [B]Emulators
[/B]

---

### Post by hook_ham on 2016-02-24
Thanks potato but looks like it is already set to OpenGL as default. Any other suggestions?

---

### Post by deadflowr on 2016-02-24
Well, thinking about it on 15.10 I had a similar problem.
the workaround for that was to edit the file:
/home/me/.pcsx/pcsx.cfg
and change the line for CPU=0 to CPU=1.
Then save and exit.

I'm not sure they are the same problem, but the behavior described is actually what was happening.

per chance could simply be a shot in the dark

---

### Post by hook_ham on 2016-02-25
Didn't seem to make a difference unfortunately. Is there no way that I can generate an error on the terminal or something?

---

### Post by deadflowr on 2016-02-26
> **hook_ham said:**
> Didn't seem to make a difference unfortunately. Is there no way that I can generate an error on the terminal or something?
Just run the command: ***pcsx***
also *pcsx -h* (for help) might list a few options; I'm on 16.04 currently so can't remember if if differs from 14.04, I'll look later.

---

### Post by The_Cysko_Kid on 2016-07-21
Just as an FYI editing the cfg file from cpu = 0 to cpu = 1 worked for me on PCSXR on Mint 18. Very nice answer thanks.

---

### Post by zandt204 on 2017-02-12
Sorry to bump this thread but I have the same issue. Im in 16.04 and just downloaded pcsx through the ubuntu app store. Where can I get to the cfg file? I tried going home/myname/ but there's no .pscx folder and I did a search through the whole computer but couldn't find the pcsx.cfg file anywhere.

---

### Post by plastiktoymachine on 2017-03-05
> **zandt204 said:**
> Sorry to bump this thread but I have the same issue. Im in 16.04 and just downloaded pcsx through the ubuntu app store. Where can I get to the cfg file? I tried going home/myname/ but there's no .pscx folder and I did a search through the whole computer but couldn't find the pcsx.cfg file anywhere.

Go to your home folder and press Ctrl+h and this will show hidden files which is what the .pcsx folder is, then you can edit the .cfg file from there. This did fix my crashing issue as opengl would crash but software render would not.

---

### Post by braincrush on 2017-07-24
> **deadflowr said:**
> Well, thinking about it on 15.10 I had a similar problem.
the workaround for that was to edit the file:
/home/me/.pcsx/pcsx.cfg
and change the line for CPU=0 to CPU=1.
Then save and exit.

I'm not sure they are the same problem, but the behavior described is actually what was happening.

per chance could simply be a shot in the dark


worked in Elementary Os Loki, thanks a lot Sir !

---

### Post by emes18 on 2018-01-20
> **deadflowr said:**
> Well, thinking about it on 15.10 I had a similar problem.
the workaround for that was to edit the file:
/home/me/.pcsx/pcsx.cfg
and change the line for CPU=0 to CPU=1.
Then save and exit.

I'm not sure they are the same problem, but the behavior described is actually what was happening.

per chance could simply be a shot in the dark

I changed the line in pcsx.cfg and this fixed the problem on my Linux Mint 18.3.

---

### Post by coffeecat on 2018-01-20
Back to sleep, ancient thread.

Closed.

---

