---
title: "Login screen resolution is wrong"
date: 2007-09-16
forum: Desktop Environments
---

### Post by runemaste644 on 2007-09-16
Hi. When I filled up my/home and didn't know what to do (I couldn't login) i dpkg-reconfigured X and messed up my default res. I have my xorg.conf file attached and my monitor should be at 1680×1050 @ 55Hz. Could someone who is very experienced edit xorg.conf to have 1680×1050 as default resolution?
I had to make it xorg.conf.txt so it would upload

---

### Post by Happy_Man on 2007-09-16
and what is it at now?

---

### Post by Stebalien on 2007-09-16
I would Change
```
Section "Screen"
 #     
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection
```
TO
```
Section "Screen"
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1860x1050@60"
    EndSubSection
EndSection
```
You may even be able to delete that section but I can't recommend this because i am not an expert.

---

### Post by runemaste644 on 2007-09-17
I don't know. The pixels are large, so it is displaying wrong, too. When you reconfigure xorg are xorg.conf 1 2 3 4 5 and 6 changed or are they backups? There is an xorg.conf.backup

---

### Post by runemaste644 on 2007-09-24
Well i do not really want to edit xorg.conf but i am sick of it being wrong.

---

