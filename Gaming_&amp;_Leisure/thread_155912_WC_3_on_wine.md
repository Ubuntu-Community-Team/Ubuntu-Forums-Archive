---
title: "WC 3 on wine"
date: 2006-04-06
forum: Gaming &amp; Leisure
---

### Post by slipk487 on 2006-04-06
has anybody gotten Warcraft 3 to work under wine because it starts the launcher and stays white and does nothing

---

### Post by localzuk on 2006-04-06
Not all Windows programs work under wine. Take a look at [http://appdb.winehq.org/appview.php?appId=897](http://appdb.winehq.org/appview.php?appId=897) for the status of this particular  application.

---

### Post by hezral on 2006-04-06
what version of wine are you using? i got it to work using the latest wine 0.9.11
and also when i launch warcraft i used the war3.exe file and not the warcraft III.exe file. the Warcraft III.exe file hangs if i use it but the war3.exe file starts the program fine. 

ps/ i also got it to work with wine 0.9.5 before i updated it.

maybe you could look here [http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine](http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine)

---

### Post by slipk487 on 2006-04-06
WC 3 1.20 c
Wine 0.9.11

i got it to work once starting war3.exe but it went so slow i couldnt move the mouse and if i start it up in opengl and gets some kind of error dont rember wat it was  but i have the recormended requirments a 
700 mhz celeron
256 Ram
128 Vineo card

---

### Post by polpak on 2006-04-06
[QUOTE=slipk487]
i got it to work once starting war3.exe but it went so slow i couldnt move the mouse and if i start it up in opengl and gets some kind of error dont rember wat it was  but i have the recormended requirments a 
[/QUOTE]


To get warcraft 3 to work under wine, you have to have your 3d accellerated video card drivers installed. 

You also have to run it with "wine war3.exe -opengl" 

And you have to use winecfg to specify that /media/cdrom0 is drive type CDROM.

After that it works great.

If I were to guess I'd say that you don't have the 3d accellerated drivers for your video card installed. What kind of card is it?

---

### Post by slipk487 on 2006-04-06
i have a ATI Radeon with the ATI Control Program installed were would i enable the 3d accrelater

---

### Post by polpak on 2006-04-06
[QUOTE=slipk487]i have a ATI Radeon with the ATI Control Program installed were would i enable the 3d accrelater[/QUOTE]


Follow the wiki:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by slipk487 on 2006-04-06
how do i tell if the 3d in enabled

---

### Post by slipk487 on 2006-04-06
[IMG]http://www.filelodge.com/files/hdd8/206324/Screenshot.png[/IMG]
here is a pic from the ATI Control

---

### Post by polpak on 2006-04-07
[QUOTE=slipk487]how do i tell if the 3d in enabled[/QUOTE]

what's the output of 
```

glxinfo | grep direct
```

---

### Post by slipk487 on 2006-04-07
direct rendering: Yes

---

### Post by slipk487 on 2006-04-07
i get this error

```
slipk487@slipk487:~$ wine "C:\Program Files\Warcraft III\War3.exe" -opengl
fixme:ole:ITypeInfo_fnRelease destroy child objects
slipk487@slipk487:~$

```

---

### Post by satyam on 2006-06-06
[QUOTE=slipk487]has anybody gotten Warcraft 3 to work under wine because it starts the launcher and stays white and does nothing[/QUOTE]

Yes, War3 The Frozen Throne CAN run under wine - and there's no perceptible difference from running it in windoze. Your problem sounds like you're not getting 3D acceleration. I assume you have 3D acceleration working in Ubuntu? Can you run fgl_glxgears?

Before I got the video acceleration working, I'd get the start screen, and it would run *really* slow; like one frame per minute.

The command I used is:
wine war3.exe -opengl

I got it to run using wine 0.9-14, in a 32-bit chroot. (I have an AMD64.) Hope this helps.

---

