---
title: "How to Configure LXDM Login Resolution"
date: 2010-08-02
forum: Desktop Environments
---

### Post by dodle on 2010-08-02
I was able to fix the desktop resolution of my Lubuntu install using xrandr and /etc/xdg/lxsession/Lubuntu/autostart.  But I cannot figure out how to change the resolution of the LXDM login screen.  It is set to 1600x1200, but my screen's max resolution is 1024x768, so I only see a portion of the login screen.  Does anyone know how to configure LXDM.  I haven't been able to find and answer googling "lxdm resolution".

---

### Post by cavalier911 on 2010-08-04
Xrandr wasn't kicking in until after your login ended and the session started. 
There may be a place to start xrandr after X starts but prior to lxdm starting.
I spent an hour trying to find it then gave up.
Remove @xrandr -s 1024X768 from /etc/xdg/lxsession/Lubuntu/autostart
This will force X to run 1024X768 from the moment it starts.
First we have to boot into recovery mode from grub menu, hold shift if menu is hidden.
After you finish booting to the recovery menu choose last selection root.
```
X -configure
``````
nano xorg.conf.new
```Scroll down almost to the bottom of xorg.conf. 
Add what's in bold and save.

```
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                **Modes     "1024x768"**
        EndSubSection
EndSection

```Move/rename
```
mv xorg.conf.new /etc/X11/xorg.conf
```Start display manager
```
lxdm
```If things go wrong and X server won't start reboot into recovery mode to fix, delete, or rename /etc/Xll/xorg.conf

---

### Post by dodle on 2010-08-06
I can't boot into grub for some reason, so I tried copying your xorg.conf, which didn't work.  I don't think LXDM uses the xorg.conf, but maybe I'm wrong.

---

### Post by kerry_s on 2010-08-06
look for /etc/lxdm

---

### Post by cavalier911 on 2010-08-06
Lxdm is just the display/login manager,same as gdm,slim,etc.. They start the xserver but don't control the video resolution,modes,timing,etc..Provided autodetection works correctly and the correct driver for your video chip is included with the distro the xorg-xserver doesn't need the xorg.conf. If you want to add a custom configuration to override the default behaviour you have to let xorg-xserver create a generic xorg.conf for your system which you then edit to control the xserver.
I posted a small portion of my xorg.conf only to illustrate the section you need to edit. Xorg-xserver can't generate the default xorg.conf when it's running,you have to be in single user mode before it has started aka recovery mode. When you say you can't boot into grub do you mean the grub menu is hidden? By default grub2 hides it's menu unless it detects more than one kernel/os on your computer.If thats the case hold the shift key down as soon as you powerup the computer starting with the bios boot,eventually the menu appears.

---

### Post by Stroman on 2010-08-07
Thank You,
I may be able to try some of this later today.
Stroman

---

### Post by dodle on 2010-08-08
> **kerry_s said:**
> look for /etc/lxdm

I have, but I can't see any way to confgure the resolution in any of the scripts.

> **cavalier911 said:**
> When you say you can't boot into grub do you mean the grub menu is hidden? By default grub2 hides it's menu unless it detects more than one kernel/os on your computer.If thats the case hold the shift key down as soon as you powerup the computer starting with the bios boot,eventually the menu appears.

Holding Shift does not do anything, and I have tried killing the xserver after I log in, but my laptop freezes up.  I tried installing GRUB legacy, but that doesn't seem to have done anything either.  It used to be that if the GRUB menu was hidden there was a short timeout that said "Press Esc" to see the menu.  But that does not appear.  

I just watched a tutorial on configuring GRUB2: [http://www.youtube.com/watch?v=OhK8sUcLgTM](http://www.youtube.com/watch?v=OhK8sUcLgTM).  I will post back what I changed if I am able to get into the GRUB menu.

---

### Post by dodle on 2010-08-08
Thank yo cavelier, your solution to configure the xserver worked.  It also fixed a problem I was having with font size.  

To get into GRUB, I had to comment out the following line in /etc/default/grub:

> GRUB_HIDDEN_TIMEOUT=0

then run:

```
sudo update-grub
```

---

### Post by elect on 2010-11-07
How configure the resolution in the Lubuntu 10.10?

---

### Post by blakeatl on 2010-12-07
> **elect said:**
> How configure the resolution in the Lubuntu 10.10?

I'm running Lubuntu and the only thing that worked for me was to run this in a command line: xrandr --output LVDS1 --mode 1024x600 --scale 1.00x1.28 --panning 1024x768. You can also paste this in /etc/xdg/lxsession/LXDE/autostart. 

I got this from another thread, so I can't take any credit....this is just me finding a solution by searching around the forum.

---

