---
title: "Howto test SLI?"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by Snipersnest on 2005-12-15
With the new nvidia drivers out that support SLI is there a way I can test my SLI to make sure its working?
 
I'm still only getting 13,000-14,000 fps on glxgears which is the normal amount for 1 card..
 
How can I check?

---

### Post by madjinx on 2005-12-15
1 make sure its enabled

2. what kind of card do you have?

3. For testing, disable and reboot, play Doom3 on really high settings, get a FPS, then enable it, reboot and do the same.

---

### Post by Snipersnest on 2005-12-15
I've got Steam installed and tested it with CS Source...I'm only seeing it with 1 video card its not adding anything.. Is this because Cedega doesn't support it or because its just not working?
 
Also I have 2 BFG Geforce 6800 GT OC cards...on an Asus A8N-SLI Premium...
 
I get well over 200fps in Source when I play in Windows and about 150fps on the video stress test but thats with 1280x1024 and all settings on high for the stress test.
 
Linux is only putting about 50-70fps...it can't be working

---

### Post by Miguel on 2005-12-15
Snipersnest... it can perfectly be working... it the bottleneck is the CPU. While you might not have anything else running, it is possible that the cedega calls cause some system overhead that makes a bottleneck with the CPU (with SLI 6800 GT's). If reducing, even drastically, resolution and detail gives you similar results... I would point to cedega overhead on the CPU

But I could be wrong... I only measure density functional theory codes.

---

### Post by Snipersnest on 2005-12-15
[QUOTE=Miguel]Snipersnest... it can perfectly be working... it the bottleneck is the CPU. While you might not have anything else running, it is possible that the cedega calls cause some system overhead that makes a bottleneck with the CPU (with SLI 6800 GT's). If reducing, even drastically, resolution and detail gives you similar results... I would point to cedega overhead on the CPU

But I could be wrong... I only measure density functional theory codes.[/QUOTE]

Well that could explain the Cedega part...But why are my glxgears scores the same as they are for a single card?? Maybe glxgears is the same way as Cedega?  I thought it would show up somehow but I can't tell at all..Everything still seems like I'm using 1 card.

I just feel like I'm wasting $300 lol...I'm about to just upgrade my wifes computer and let her use it.

---

### Post by Miguel on 2005-12-16
Hi Snipersnest,

Even though the glxgears thing is suspicious, it is not a definitive nay to SLI. You know, glxgears is not a benchmark. However, odds are SLI isn't working in your system.  Anyway, the definitive test would be running a native game. If you don't have any, you can download Quake4 demo or Doom3 demo and test it at various high settings. Then, compare it with the FPS you got with one card or with the previos drivers.

OT: While it is a bit harsh, I do think that SLI is slightly overvalued. I mean, how much faster are 2 SLI'ed GF 6800GT's than a 6800 Ultra? Are they faster than a 7800GT?. While you might get somewhat better performance at ultra high quality, the price for it is a tad too high for me. If you plan to play online with your wife to some demanding games... it might be a good idea to use the second 6800 in her computer (at least it will be cheaper than a new one!)

---

### Post by Snipersnest on 2005-12-16
[quote=Miguel]Hi Snipersnest,
OT: While it is a bit harsh, I do think that SLI is slightly overvalued. I mean, how much faster are 2 SLI'ed GF 6800GT's than a 6800 Ultra? Are they faster than a 7800GT?. While you might get somewhat better performance at ultra high quality, the price for it is a tad too high for me. If you plan to play online with your wife to some demanding games... it might be a good idea to use the second 6800 in her computer (at least it will be cheaper than a new one!)[/quote]
 
Well the good part about buying the BFG 6800 GT OC cards is you can overclock them more if you have a good case that keeps them cool... I've gotten mine perfectly stable on stock heatsink and fan with the 400/1100 setup.. I'm about to order my water cooling and I should be able to push 440/1270... 
 
So yes for the cheaper price to answer your question...they are faster than the 7800...plus 7800 are over rated do to the fact only 2 games support them and the drivers barely back them up...hell the drivers barely support my 6800's.  My water kit is from Danger Den and its going to cost about $560 w/shipping in my Thermaltake Shark case..
 
I will d/l the Quake 4 demo tonight and give it a try. I guess its the only way I'll be able to tell if its working.

---

### Post by PsyberOneZero on 2005-12-16
Stupid question but, did you enable sli in your xorg.conf?
```
Option "SLI" "Auto"
```

[quote=NVIDIA Readme]
Q. Why is glxgears slower when SLI is enabled?

A. When SLI is enabled, the NVIDIA driver must coordinate the operations of
   both GPUs when each new frame is swapped (made visible). For most
   applications, this GPU synchronization overhead is negligible. However,
   because glxgears renders so many frames per second, the GPU synchronization
   overhead consumes a significant portion of the total time, and the
   framerate is reduced.


Q. Why is Doom 3 slower when SLI is enabled?

A. The NVIDIA Accelerated Linux Driver Set does not automatically detect the
   optimal SLI settings for games such as Doom 3 and Quake 4. To work around
   this issue, the environment variable __GL_DOOM3 can be set to tell OpenGL
   that Doom 3's optimal settings should be used. In Bash, this can be done in
   the same command that launches Doom 3 so the environment variable does not
   remain set for other OpenGL applications started in the same session:
   
       % __GL_DOOM3=1 doom3
   
   Doom 3's startup script can also be modified to set this environment
   variable:
   
       #!/bin/sh
       # Needed to make symlinks/shortcuts work.
       # the binaries must run with correct working directory
       cd "/usr/local/games/doom3/"
       export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
       export __GL_DOOM3=1
       exec ./doom.x86 "$@"
   
   This environment variable is temporary and will be removed in the future.
[/quote]

---

### Post by brainkilla on 2005-12-16
Snipersnest, you need to enable SLI mode in your xorg.conf by adding 

```
 Option "SLI" "Auto" 
```

in the Device section. Restart your xorg (ctrl+alt+backspace) and launch nvidia-settings from a terminal. You should then see entries for both of your cards, and consequently you can start fraggin' ;). Hope I helped...

---

