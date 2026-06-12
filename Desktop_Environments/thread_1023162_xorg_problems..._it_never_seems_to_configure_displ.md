---
title: "xorg problems... it never seems to configure displays/adapters"
date: 2008-12-27
forum: Desktop Environments
---

### Post by Underpants on 2008-12-27
It seems like ubuntu 8.10 really hates Intel built in graphics adapters, which I have in a lot of systems.


After installation all I get is this in the xorg.conf

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```



This is a pain in the **** for me, because I use ubuntu in a headless configuration for most of my systems and just use x11vnc to control the console. If there isn't a monitor attached with that configuration, ubuntu starts in "low graphics mode" which might as well be "fook you mode"

I'm a long time user of linux and haven't ever spent any time working with xorg but since these video cards have almost always been detected in the past... i feel a little ripped off :(

---

### Post by Zorael on 2008-12-27
It does that nowadays. Instead of relying on xorg.conf to explicitly tell it about your system, it uses HAL to autodetect it instead.

Does it boot up in some form of safe mode or just in 800x600 as a fallback resolution? I mean, in the latter case you could just use 'xrandr -s 1280x1024', or whatever resolution you may want, when you want it.

---

### Post by Underpants on 2008-12-27
It comes straight to a prompt about "low graphics mode" No GDM, which means that x11vnc wont launch. :/ 

I will look into that command.

---

### Post by Zorael on 2008-12-27
Hmm, see [http://ubuntuforums.org/showthread.php?p=6444978](http://ubuntuforums.org/showthread.php?p=6444978) and [https://bugs.freedesktop.org/show_bug.cgi?id=14611](https://bugs.freedesktop.org/show_bug.cgi?id=14611). So you're not alone. Perhaps changing to the vesa driver like the first link suggests would help.

---

