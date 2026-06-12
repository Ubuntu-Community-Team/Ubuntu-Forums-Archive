---
title: "Broken minimized window"
date: 2020-06-07
forum: Desktop Environments
---

### Post by tommimon on 2020-06-07
I'm using Ubuntu 20.04 LTS with default gnome.

I have a recurrent problem with my minimized windows that sometimes happens wile I'm messing app with multiple windows but I'm not able to identify the cause.
I'm using the "dash to panel" extension, don't know if this could be the cause.

[SIZE=3]**Description of the problem:**[/SIZE]
A window that was minimized shows up also if it is not suppose to and I can't interact in any way with it (can't click anything).
The only way I found to make it work again is to click the icon in the dash, this reopen the window as if it was minimized (but I was already seeing it).
Unfortunately "reopen" this make other strange things append like other minimized windows showing up and freezing in the same way.
This continues until I reopen all the windows and minimize all again and it is an huge waste of time.

[SIZE=3]**Possible triggers identified:**[/SIZE]
Sometimes it happens when I minimize all the windows with Super+D or the right-down corner but not always.
I believe sometimes I triggered this showing the preview of a window hovering with the mouse and than switching to another window.

To be clear this is something happens multiple times per day so there has to be something wrong with my system.
How can I stop this?

--EDIT--
Actually found an easy way to reproduce this: hover an icon so that the app preview shows and hit Super+D.

---

### Post by CelticWarrior on 2020-06-07
Welcome.

Please post the hardware specifications, namely the graphics. It's very likely related to graphics drivers.

---

### Post by tommimon on 2020-06-07
OS: Ubuntu 20.04 LTS x86_64 
Kernel: 5.4.0-33-generic  
Packages: 2066 (dpkg), 21 (snap) 
Shell: bash 5.0.16 
Resolution: 1920x1080 
DE: GNOME 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru-dark [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i5-6400 (4) @ 3.300GHz 
GPU: NVIDIA GeForce GTX 970 
Memory: 5503MiB / 15945MiB

---

### Post by CelticWarrior on 2020-06-07
```
GPU: NVIDIA GeForce GTX 970
```

So, install Nvidia drivers. Open Additional Drivers, wait..., select and apply the recommended version which is likely the newest drivers version. Reboot.

---

### Post by tommimon on 2020-06-07
I see "This device is using the recommended driver".
Is this problem something known in ubuntu or it's only me?

---

### Post by CelticWarrior on 2020-06-07
It's only you, so far.

Please check UEFI settings and assure Secure Boot is disabled.

---

### Post by tommimon on 2020-06-07
Secure Boot is disabled.
I tried the same thing on my laptop and I have the same problem using Ubuntu 20.04 and dash-to-panel 31 as in my main computer.
AFAIK I have this problem only with dash-to-panel turned on and only if you have any kind of preview option: as the window peeking option or reveal desktop when hovering (for desktop button).
Seams to be a bug of dash-to-panel but as temporary solution I disabled those options but this should not be necessary.
I'm wondering if installing a newer version than 31 could fix the bug but from apt I can install only this, the newest is the 37 can I get it on ubuntu somehow?

Dash to Panel repo:
[https://github.com/home-sweet-gnome/dash-to-panel](https://github.com/home-sweet-gnome/dash-to-panel)

---

### Post by rhyshowitt on 2020-07-10
I have this bug too, and as far as I know I don't have dash-to-panel.  My google searching so far says there were similar issues around 2012.  I will keep looking.

---

