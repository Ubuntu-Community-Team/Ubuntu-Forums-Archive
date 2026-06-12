---
title: "lost gui, stuck at command line"
date: 2009-01-14
forum: General Help
---

### Post by DiGiTY on 2009-01-14
Via Ubuntu package manager GUI I removed anything nvidia and xserver-xorg-nv installed to troubleshoot an unrelated problem and now after restarting I get a low resolution error message/window. "dpkg-reconfigure xserver-xorg" doesn't help as it only configures video frame buffer and keyboard and nothing about the video card or resolution. also my xorg.conf is pretty bare (see below).

how do I get Ubuntu to bop back up with my Gnome desktop?


```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
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

---

### Post by Zaki ur Rehman on 2009-01-14
I am also facing the problem when ever I am going to command line by pressing cntrl+alt+f1 I cant come back at GUI.

---

### Post by DiGiTY on 2009-01-14
I fixed the problem with the command below. it looks like I mucked up initially by removing some core xserver-xorg component along with packages with nvidia in their names.

```
apt-get install x-window-system-core xserver-xorg gnome-desktop-environment
```

---

### Post by balaknair on 2009-01-14
@DiGiTY

Good to see you got it figured out.
I was gonna suggest 'sudo apt-get install ubuntu-desktop' so that apt-get would install the missing X dependencies as well.

@Zaki ur Rehman:

Did you try cntrl-alt-F7 to get back into the GUI?
Unless you stopped the GUI completely, it's still running in the background.
cntrl-alt-F1 to F6 ---> Text consoles
cntrl-alt-F7 + ---> GUI console(X Windows console)

---

