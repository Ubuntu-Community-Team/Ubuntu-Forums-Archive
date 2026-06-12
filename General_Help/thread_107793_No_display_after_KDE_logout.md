---
title: "No display after KDE logout"
date: 2005-12-24
forum: General Help
---

### Post by wins on 2005-12-24
Just installed Kubuntu 5.10 yesterday, everything working great after some tweaking, except whenever I perform logout/reboot/shutdown from KDE, my LCD goes black and says "No display". It does not give me back the login screen, pressing ctrl-alt-backspace doesn't give me back the console login either. I have also tried to switch default init level from 2 to 3, doesn't help.
I have tried apt-get full upgrade, the problem is still there.

The /var/log/Xorg.0.log show these messages after KDE logout:

(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d5d000 at 0xb7ae2000
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) fglrx(0): UMM Bus area:     0xb0701000 (size=0x078ef000)
(II) fglrx(0): UMM area:     0xb0701000 (size=0x078ef000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:5:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

I can't do anything after that, except Ctrl-Alt-Del to reboot the PC. :(

I am using ATI X700 display card, and installed the ATI fglrx driver as described in 

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Any help is highly appreciated. Thx.

---

### Post by mlomker on 2005-12-26
That's a common problem with fgrlx.  You could try the [latest driver]("http://ubuntuforums.org/showpost.php?p=423584") but I don't know if that'll resolve it or not.

---

