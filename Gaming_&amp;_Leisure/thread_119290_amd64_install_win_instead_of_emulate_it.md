---
title: "amd64: install win instead of emulate it"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by Josef K. on 2006-01-19
since wine\cedega doesn't work on amd64 and I got enough power (3300+1Gbram), I wonder if installing winxp in ubuntu (using qemu or win4lin or whatever...) would be a solution to play win games instead have a dual boot system
any experience?

---

### Post by michealm on 2006-01-19
[QUOTE=Josef K.]since wine\cedega doesn't work on amd64 and I got enough power (3300+1Gbram), I wonder if installing winxp in ubuntu (using qemu or win4lin or whatever...) would be a solution to play win games instead have a dual boot system
any experience?[/QUOTE]

I wouldnt reccomend this, as most Virtual OS Emulators like win4lin and qemu, use a emulated generic video driver for video output and i think they dont support DX9, or HW Acceleration.

---

### Post by tekwarren on 2006-01-19
Is there a projection of when wine or cedega will be available for 64bit? I'm still a newb with linux but am really thinking of moving and taking advantage of the new architecture...and I'm also a gamer in my free time.

---

### Post by Azion on 2006-01-19
Michealm has a point, as far as I know they won't run DX9.
Which is useless as nearly all games use it now a days.

---

### Post by leech on 2006-01-19
There is experimental 3D support in VMware, but I don't know how well it works.

Leech

---

### Post by Josef K. on 2006-01-20
I'm confused
with (k)qemu you install a complete OS (in fact you need a full copy of win and a partition to put in)
in the new OS can't you install the driver like every other sw? :confused:

---

### Post by jon_z on 2006-01-20
wine can be installed on 64 bit systems, it takes a lot of fiddling,  reasearch it in the forums...a lot of it is forcing the arch type, which is fun ;)

I searched for you

> There is a howto here:
[http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot)
It is for hoary, so replace hoary with breezy everywhere. It lets you install a 32-bit file system and any 32-bit program including wine. But if wine is the only 32-bit program that you need, then maybe chroot is overkill.
32-bit wine works in ubuntu 64 bit. Just download the .deb and install it with:
**dpkg -i --force-architecture the_file.deb**

---

### Post by slinga on 2006-01-23
I've resorted to dual booting SuSE 10.0 and (k)ubuntu 5.10. On SuSE I can install the 32 bit wine binary with no problems and I can play Stepmania...On Kubuntu everything is noticeably faster. Yeah I know a lousy workaround, still better than dual booting with Windows...

---

### Post by Elvish Legion on 2006-01-23
[QUOTE=Josef K.]since wine\cedega doesn't work on amd64 and I got enough power (3300+1Gbram), I wonder if installing winxp in ubuntu (using qemu or win4lin or whatever...) would be a solution to play win games instead have a dual boot system
any experience?[/QUOTE]


When I installed under 64 bit I had no issues with cedega...what error are you having?

---

### Post by Josef K. on 2006-01-30
my fault (tried to compile wine instead of force-architecture the deb package!) :rolleyes:

note that forcing architecture wine deb first time I got a missing library error that I solved (TKS RAOF) extracting manually libXxf86dga from the 32bit package, putting in wine directory and launching ldconfig

force-architectured cedega installation was clear :KS

---

### Post by Kuprin on 2006-01-31
If you've got a WinXP license, just dual-boot, as far as I'm concerned. Cedega...well, I don't like it because of the stunt they pulled on the Wine guys, kupo. They're no better than M$ for business "ethics".

Not that it matters for long...Windows Source Code Release + Wine Devs = :D KUPOPO! :D

---

### Post by handy on 2006-02-02
[QUOTE=tekwarren]Is there a projection of when wine or cedega will be available for 64bit? I'm still a newb with linux but am really thinking of moving and taking advantage of the new architecture...and I'm also a gamer in my free time.[/QUOTE]


There is no plans to produce Wine/Cedega  in 64bit, due to the fact that all the windoze games are 32bit.

---

### Post by peteguhl on 2006-04-17
[QUOTE=handy]There is no plans to produce Wine/Cedega  in 64bit, due to the fact that all the windoze games are 32bit.[/QUOTE]

Ever hear of Half-Life2 and Counter-strike Source?

---

