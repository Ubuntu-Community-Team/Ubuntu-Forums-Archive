---
title: "install kubuntu with xgl and compiz in vmware?"
date: 2006-03-30
forum: Desktop Environments
---

### Post by Digitallysick on 2006-03-30
Can i do this? i tried to follow the xgl and compiz guide but it crashed the whole works, is there a guide for doing this in wm workstation?

---

### Post by Dr. Nick on 2006-05-08
[QUOTE=Digitallysick]Can i do this? i tried to follow the xgl and compiz guide but it crashed the whole works, is there a guide for doing this in wm workstation?[/QUOTE]

I know this is late, but I just stumbled on it and thought I would give my opinion for anyone who finds this in the future.

I don't believe this to be possible due to vmware emulating a non nvidia/ati video card. My last experiences with vmware/virtual pc it would always emulate a very basic non 3d accelerated card and their was no way to change that. Xgl and Compiz need 3 hardware to be useable and vmware doesnt provide this.

---

### Post by pobox90210 on 2007-12-26
Bummer. Thanks for that. Shame as VMWare is perfect for playing with new installations. BAck to the drawing board.

---

### Post by DaZjorz on 2008-03-22
I read VMWare supports 3D accelleration and all that since beta 5.5, so things like this should be possible. I'm trying to figure out how to do it too...

---

### Post by napauleon on 2008-03-27
already found out how to get the 3d accelaration support working? I can't wait to use compiz in vmware!

---

### Post by SteveDC on 2008-03-28
> already found out how to get the 3d accelaration support working? I can't wait to use compiz in vmware!

Make that two of us,,,

---

### Post by bharadwaj on 2008-03-28
how about vbox? you think it can compete with vmware?

---

### Post by ZaM0 on 2008-07-13
Anyone succeed in running Compiz in VMWare? It seems that you can enable hardware acceleration with these options in the config file: 
```
mks.enable3d = "TRUE"
svga.vramSizesvga.vramSize = "67108864"
```
where "67108864" is the size for the vram.

---

