---
title: "DVD Decrypter through Wine"
date: 2005-12-21
forum: General Help
---

### Post by rjpa on 2005-12-21
Hi,

I try to install DVD Decrypter through Wine (.93), I use this code to install it:

```
#wine SetupDVDDecrypter_3.5.4.0.exe
```

but I get this error message:

```
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_DK' was not recognized, defaulting to 'en_US'.
Warning: could not find DOS drive for current working directory '/tmp', starting in the Windows directory.
wine: cannot find 'SetupDVDDecrypter_3.5.4.0.exe'
```

What is wrong here??

Cheers

---

### Post by bigzak on 2005-12-21
Put the file somewhere inside your artificial windows hierarchy (e.g. ~/.wine/drive_c) and then start it with the fully qualified windows path. e.g.

```

$ cp SetupDVDDecrypter_3.5.4.0.exe ~/.wine/drive_c
$ wine c:/SetupDVDDecrypter_3.5.4.0.exe

```

This assumes that your wine root is in ~/.wine/drive_c - check first :)

---

### Post by rjpa on 2005-12-21
Have that, but when I execute DVD Decrypter.exe it cannot find any of my drives, I've set the OS to WINNT 4.0, any ideas?

Cheers

---

### Post by ape on 2005-12-21
use the winecfg program and modify the drive type (for your CD/DVD drive(s)) to be a CD-ROM.  By default all of the CD/DVD drives that are on my systems get defaulted to Local Hard Disk.  Once I switched them to CD-ROM, DVD Decrypter was able to see them correctly.

---

### Post by Badojo on 2005-12-21
Isnt that program now like illegal to use or something I tried going to the link to download it and something came up saying the programs now illegal. If it really is illegal I would advice switching to something legal.

---

### Post by BathroomNinja on 2005-12-21
[QUOTE=Badojo]Isnt that program now like illegal to use or something I tried going to the link to download it and something came up saying the programs now illegal. If it really is illegal I would advice switching to something legal.[/QUOTE]


It depends on where you live and the laws of where you live.  In the USA, *any* dvd decryption program is illegal.

---

### Post by Badojo on 2005-12-21
[QUOTE=BathroomNinja]It depends on where you live and the laws of where you live.  In the USA, *any* dvd decryption program is illegal.[/QUOTE]

Yea thats where I live, it shouldnt be illegal considering its such a small app that can be used to burn isos. Thats why I like it anyways other apps can be stressful for burning the iso (roxio).

---

