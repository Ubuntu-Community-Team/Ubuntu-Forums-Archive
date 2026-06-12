---
title: "Can't run OpenGL programs?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Patsoe on 2006-06-05
I have a very peculiar problem - this thing just worked in Breezy... 
I'm running a fresh install of Dapper, AMD64.

It seems there's no hook for running OpenGL software - I understand very little of this so forgive the formulation. 

The best information I know to provide you with now is the output of the testprograms glxgears 
```
Error: couldn't get an RGB, Double-buffered visual
``` 
and glxinfo 
```
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

Thanks for helping out!

---

### Post by Patsoe on 2006-06-05
I can't seem to find any information that applies to this error; I tried a web search for "couldn't find RGB GLX visual" and variations of that, but nothing seems related much.

The strange thing is, I can't change the result by changing drivers; I switched from the "ati" to the "vesa" driver with no luck. The "fglrx" driver didn't help either (and introduces other problems, such as a system freeze when I go to a console).

Please tell me if I need to supply more/better information.

---

### Post by Patsoe on 2006-06-06
Hope nobody hates me for bumping this thread... it's just that I really would like to have this functionality going to test some of my work.

Some new information - I compared my xorg.conf with my previous version that Breezy used, and noticed that the only notable difference was the line loading libGLcore:
```
load    "GLcore"
```
so I added that to the new file. However, it doesn't help, neither with the "ati" nor with the "vesa" driver (which I used in Breezy).

---

### Post by lord.john.marbury on 2006-06-07
The same happens to me, in a Compaq V5054EA with a thurion and Ati X200M. I've found somewhere that this may be a bug related to the amd64 port of ubuntu :( If so, I hope that it'll be fixed soon.

PS: BTW, have you tried Dapper for 32 bits? I'll do that as soon as I can. I was also wondering of installing the Breezy Xorg packages, but I've just realised that without the "noaccel" option the system hangs at xorg's startup...

---

### Post by Patsoe on 2006-06-07
Thanks for your support, and sorry that you're stuck with it too... :( 

I haven't tried Dapper in 32bit. I know it was working in both the i386 and amd64 versions of Breezy. I'd really like to stay with the amd64 flavour now, since I'm doing some particle dynamics stuff which benefits from either the extra register size or just from the extra registers, I don't know which :P

I guess that grafting Breezy's Xorg on Dapper would get very very messy... and what's with the "noaccel"? I don't have such a line in my conffile?

By the way, I've filed a bug report here: [https://launchpad.net/bugs/48758](https://launchpad.net/bugs/48758)

---

### Post by Huffers on 2006-06-15
the reason the system freezes when you go to the console with the fglrx driver is because the fglrx driver only supports 24 bit colour mode, and your tty is likely set to use some other mode.

try editing /boot/grub/menu.lst and adding

vga = 792

to the kernel line.

---

### Post by Patsoe on 2006-06-15
Thanks Huffers, and I'm sorry - I should have updated this thread, but it sunk so far down the list that I didn't see it anymore...

In fact I've seen no more crashes with the fglrx driver since I completely removed the driver (purge) and reinstalled it from the multiverse repository. The first time, I had it installed through the Easyubuntu script - but now I'm not sure if that uses the official repositories at all...

Switching to a console should not involve the fglrx driver by the way: it is only used by the X server I think. The console remains available even if you "rmmod fglrx".

After reinstalling the fglrx driver, I also have GLX working now, with hardware acceleration! The ati  and vesa drivers still refuse to display GLX stuff, whereas I'd expect them to fall back on mesaGL. Therefore I have left the bug report up at launchpad (though updating it to say that fglrx works).

---

