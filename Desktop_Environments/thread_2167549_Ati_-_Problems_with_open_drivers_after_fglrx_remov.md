---
title: "Ati - Problems with open drivers after fglrx remove"
date: 2013-08-14
forum: Desktop Environments
---

### Post by jack_walker on 2013-08-14
Hi,

I have ubuntu 13.04 and kde 4.10.5.
I removed my fglrx drivers to upgrade to kernel 3.10.6.

After reboot my maximum display resolution was 1280x1024, but my real maximum (that I correctly had with fglrx drivers) is 1920x1080.

I tried to read this wiki: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to section "Setting resolution changes in xorg.conf -- resolution lower than expected" but it didn't solve my problem, infact I tried to edit **xorg.conf **with the following lines:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
->        SubSection "Display"
->                Virtual 3600 1200
->        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```
and after reboot it says that my xorg.conf is not correctly configured and I had to remove xorg.conf and use the old one I had backed up before.

Besides I have "plasma-desktop" crash at startup (only without fglrx drivers, that is with open drivers).

I'll give you some information:
[B]
Crash log[/B] in "Developer Information" section of KDE Crash Assistant:
[http://pastebin.com/raw.php?i=8stmVCky](http://pastebin.com/raw.php?i=8stmVCky)

Output of *glxinfo | grep -i opengl*
```
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string: 2.1 Mesa 9.0
OpenGL shading language version string: 1.20
OpenGL extensions:

```

**xorg.conf**:
[http://pastebin.com/raw.php?i=D6MPUEZv](http://pastebin.com/raw.php?i=D6MPUEZv)

**Xorg.0.log**:
[http://pastebin.com/raw.php?i=dWDVe03t](http://pastebin.com/raw.php?i=dWDVe03t)


I hope you can help me.

Thanks

---

