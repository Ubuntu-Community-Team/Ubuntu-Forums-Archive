---
title: "UT2004 in Feisty"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by lingenfr on 2007-06-02
I installed UT2004 in Feisty using the linux installer that came on the CD. Then I used the loki mega installer. I have KDE 3.5.7 and am using the intel video driver and direct rendering is working. My machine is a Toshiba Libretto U100. When I launch ut2004, the screen blanks, x pukes and I am back to a login screen. Has anyone got this working?

---

### Post by Silenus on 2007-06-02
Do you have the drivers for it? A bit more info on your rig to please, but if all else fails you can try this it's basically a ut clone. Open Arena 
openarena - A fast-paced 3D Ego-Shooter
openarena-data - OpenArena game data
openarena-server - Game server for the game OpenArena

Those are the files for it if you need it all.

---

### Post by lingenfr on 2007-06-02
I don't know what drivers you are talking about? I have video drivers (intel) with 3D rendering working. I have sound (ALSA). Is there something else I am missing? Thanks for the tip on the other game.

---

### Post by aidanr on 2007-06-02
can you post ~.ut2004/system/ut2004.log

and also check /var/log/Xorg.0.log

---

### Post by lingenfr on 2007-06-03
The ut2004 log was empty. I copied just the errors and warning from my Xorg log:

(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) intel(0): Unable to read from DVOI2C_E Slave 236.
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(II) intel(0): Allocating 4860 scanlines for pixmap cache
(WW) intel(0): Failed to allocate texture space.
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       small DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
	(Cannot allocate memory)


These seem to be some common errors with intel drivers, but I could not find a lot of info. glxinfo says direct rendering is working and glxgears runs with about 450fps. Thanks for any assistance.

---

### Post by lingenfr on 2007-06-10
Well, thanks to Open Arena, I found the first part of the problem. I needed to enable framebuffering. That allows to me launch ut2004, but it is so ridiculously slow that I can't even play a single player game. Oh well. Open Arena is a decent substitute for the time being.

---

### Post by Ferrat on 2007-06-10
You need to install a real grafic driver 

Guessing you have a ATi card but don't have the ATi drivers that they supply?

---

### Post by lingenfr on 2007-06-17
> **Ferrat said:**
> You need to install a real grafic driver 

Guessing you have a ATi card but don't have the ATi drivers that they supply?

You don't have to guess, I told you it was an intel card (855GM) in the first post. FWIW, I have not been about to get it to work adequately with my ATI Mobility Radeon 9600 either and I downloaded and compiled the *graphic* driver for it.

---

### Post by johnny4north on 2007-06-17
check out this link you might be able to get 25fps improvement for ut2004 - [http://www.ataricommunity.com/forums/showthread.php?s=&threadid=357981;](http://www.ataricommunity.com/forums/showthread.php?s=&threadid=357981;))

---

### Post by lingenfr on 2007-06-28
That looks a bit complicated, but I will try it as I have time. I loaded it on my P4 3.0 with ATI 9550 (cheapo) and it works pretty well. Don't know if it is the processor or the graphics, but it runs pretty good.

---

