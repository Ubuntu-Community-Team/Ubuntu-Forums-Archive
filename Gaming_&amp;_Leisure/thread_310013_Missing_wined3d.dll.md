---
title: "Missing wined3d.dll"
date: 2006-11-30
forum: Gaming &amp; Leisure
---

### Post by Vord on 2006-11-30
I'm trying to install WoW through WINE and the main source of the last error that I'm getting is the fact that I'm missing wined3d.dll, I can't find it to download, so could someone link me to a download mirror, or possibly send the .dll to me? I've spent too long on this to have it not work

---

### Post by Vord on 2006-11-30
Bump? Please? I really need to get this working, I've spent about 13 hours trying to get this god damned program to install, and this is probably the only thing stopping me.

---

### Post by Vord on 2006-11-30
](*,) I'm heading out to class, if someone could PLEASE just take their wined3d.dll and upload it to a mirror for me, or just tell me how to get it into my wine/drive_c/windows/system32 folder, please do. Thanks.

---

### Post by qrm on 2006-11-30
you could atleast try looking around in the forums...

[http://ubuntuforums.org/showthread.php?t=300253](http://ubuntuforums.org/showthread.php?t=300253)

you wont be needing the wined3d.dll because you have to configure it to use OpenGL

---

### Post by Vord on 2006-11-30
That's the guide I've been using, but the error I get when trying to start WoW.exe says that I'm missing that .dll. I'm just trying to fix the error at this point. You said you configure it to run on OpenGL, where in the guide does it say anything about that? I possibly missed it but I've combed the guide more than a few times, and saw no mention of it.

---

### Post by hikaricore on 2006-11-30
> **Vord said:**
> That's the guide I've been using, but the error I get when trying to start WoW.exe says that I'm missing that .dll. I'm just trying to fix the error at this point. You said you configure it to run on OpenGL, where in the guide does it say anything about that? I possibly missed it but I've combed the guide more than a few times, and saw no mention of it.

WoW starts in Direct3D mode automaticly unless you edit your config.wtf file or start it with a command such as:

```
wine WoW.exe -opengl
```

---

### Post by Vord on 2006-11-30
Running wine WoW.exe -opengl yields the same exact error, I have no idea where to go from here.

---

### Post by hikaricore on 2006-11-30
> **Vord said:**
> Running wine WoW.exe -opengl yields the same exact error, I have no idea where to go from here.

Are you by any chance building from source in edgy?

I had a similar issue I almost forgot about.

For some reason anytime I build wine from source it's broke to ****.

I solved this issue by uninstalling wine with the source:

(in the source directory)

```
./configure
sudo make uninstall 
```

then installing the ubuntu builds from budgetdedicated

```
wget http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.26~winehq0~ubuntu~6.10-1_i386.deb
sudo dpkg -i wine_0.9.26~winehq0~ubuntu~6.10-1_i386.deb

```

Personally I don't have a file called wined3d.dll anywhere, but there is a wined3d.dll.so in the /usr/lib/wine/ directory, which I've attached to this message.

Hopefully I've been of some help here.

Enjoy.

---

