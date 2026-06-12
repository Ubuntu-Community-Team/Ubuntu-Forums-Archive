---
title: "Stuck at 640x480 resolution after using Win 2000"
date: 2005-11-27
forum: Desktop Environments
---

### Post by gergbee on 2005-11-27
Hi, 

After I use Windows 2000 and reboot into Ubuntu, my resolution is stuck at 640x480 and I cannot change it.  If I shut down the system completely and wait for a while, the problem will correct itself.  Perhaps I am angering the Ubuntu gods by using Win 2000 and this is my punishment, but it's still a pain to have to shut down and wait.

Anyone have any suggestions on how to fix this?  

Greg

---

### Post by cdhotfire on 2005-11-27
[quote=gergbee]Hi, 

After I use Windows 2000 and reboot into Ubuntu, my resolution is stuck at 640x480 and I cannot change it. If I shut down the system completely and wait for a while, the problem will correct itself. Perhaps I am angering the Ubuntu gods by using Win 2000 and this is my punishment, but it's still a pain to have to shut down and wait.

Anyone have any suggestions on how to fix this?  

Greg[/quote]

```

$ sudo gedit /etc/X11/xorg.conf

```

Look for this section
```

Section "Screen"
..........................
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

```

Have it look like this

```

    SubSection "Display"
        Depth        24
        Modes        "1280x1024" 
   EndSubSection

```

Change 1280x1024 to what ever resolution you want.

---

### Post by gergbee on 2005-11-27
[QUOTE=cdhotfire]```

$ sudo gedit /etc/X11/xorg.conf

```

Look for this section
```

Section "Screen"
..........................
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

```

Have it look like this

```

    SubSection "Display"
        Depth        24
        Modes        "1280x1024" 
   EndSubSection

```

Change 1280x1024 to what ever resolution you want.[/QUOTE]

I tried that but it still came up in low resolution.  This time even a long shut down didn't help, I booted up in recovery mode then rebooted and it cleared up.

Should I change the modes for every colour depth possible?

---

### Post by jgbiggs on 2005-11-28
I am having the same problem.  Except mine is not a dual-OS booting machine.  I have edited the /etc/X11/xorg.conf file to only allow the display to use 24 bit color and 1280x1024 resolution (native for my lcd.)

Is there any other place in the system where this resolution is set?  any gdm settings?

If I do a ctrl-alt-backspace and loging and start x in a new session, I am at the correct resolution.

Any ideas?

---

### Post by DrBair on 2005-11-29
I have the same issue if and only if the monitor is not on when the machine is booting up.  If I do not have it on its in 640x480 res and pressing ctrl-alt-bksp (restarts the X server) always fixes it.  

If this is not the case for you, your monitor might be returning bad DDC info (essentially the monitors capable resolutions and refresh rates) and there is a way to disable X from checking it.  

Although this behavior seems annoying, you'd come to appreciate it after working on windows machines and older LCD monitors all the time.

---

### Post by jgbiggs on 2005-11-30
aahhh, now it makes sense.  I have this machine set up on a KVM switch with my WinXP box.  The WinXP box is computer #1 (default) and Linux is #2.

So when I hit the power to boot up both, the winxp box has control of the monitor.  Leaving the linux box to assume I don't have a monitor hooked up.

How do I disable this "checking?"

Thanks for the heads-up.  I didn't have this issue with FC4.

---

### Post by frodon on 2005-11-30
[QUOTE=gergbee]Hi, 

After I use Windows 2000 and reboot into Ubuntu, my resolution is stuck at 640x480 and I cannot change it.  If I shut down the system completely and wait for a while, the problem will correct itself.  Perhaps I am angering the Ubuntu gods by using Win 2000 and this is my punishment, but it's still a pain to have to shut down and wait.

Anyone have any suggestions on how to fix this?  

Greg[/QUOTE]All of you here who get resolution problems could you please post the exact name of your screen and attach to the post your xorg.conf file ?

In most of the case all the resolution problems are solved by putting in the xorg.conf the good horizontal and vertical refresh rates corresponding to your screen.

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

