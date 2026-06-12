---
title: "Ubuntu 22.04 not loading Desktop, completely unusable."
date: 2023-05-04
forum: Desktop Environments
---

### Post by darolu on 2023-05-04
Ubuntu 22.04 was running fine for over a year now, a month ago started giving me trouble on loading the GUI, I could restore it from Recovery Mode by reinstalling ubuntu-desktop package, I tried again but I still can't get onto desktop.
GRUB loads fine, and when Ubuntu is loading it just halts at a black screen, completely unresponsive. I can't go to any TTY. Recovery mode works, loading desktop from there (safe graphics mode I guess) works but is almost unusable due extremely low resolution (640x480 iirc). I've also tried deleting lock files to reconfigure dpkg, update everything and reinstall ubuntu-desktop again but I keep getting stuck at that black screen.
How can I solve this?
Thanks in advance.

---

### Post by ajgreeny on 2023-05-04
See ***System-Info-Script*** in my signature below and follow that to download and run the script. Post the results pastebin link back here.

If that seems to much hassle run command
***inxi -Fzx***
and post the output back here using Code Tags.  There's a how to in my signature below

That will tell us all about your hardware and software and give us some clues to the problem. I suspect a graphics driver is possibly causing this but with no information it's impossible to know at the moment.

---

### Post by darolu on 2023-05-05
Thanks for the reply.

Here's the link: [https://paste.ubuntu.com/p/P8hgJRPfRq/](https://paste.ubuntu.com/p/P8hgJRPfRq/)

Hopefully you'll be able to help me solve (or diagnose) this from that. :D

---

### Post by ajgreeny on 2023-05-05
Thanks for that link.
Unfortunately, I'm no expert in this, but I can find no mention of graphic driver in the report so I can't help further.

There may be others who can find your problem so don't despair just yet but wait for more eyes to view the thread.

The other option as I mentioned in my last post is to run that command ***inxi -Fzx*** and copy back here the output you see, again using code tags please.

---

### Post by ActionParsnip on 2023-05-05
```

  *-display UNCLAIMED
       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6850]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: 
           memory:d0000000-dfffffff 
           memory:fddc0000-fdddffff 
           ioport:ee00(size=256) 
           memory:c0000-dffff

```

May be the culprit

---

### Post by darolu on 2023-05-05
Thank you for your replies.

If anyone can tell me what logs may record this error (apparently gfx card-related) would be much appreciated.

I'm really trying to avoid reinstalling everything (last time I did was for 20.04), so any hint on how to find the issue is welcome.

```

:$ inxi -G
Graphics:
  Device-1: AMD Barts PRO [Radeon HD 6850] driver: N/A
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: ati,vesa unloaded: fbdev,modesetting,radeon
    gpu: N/A resolution: 640x480
  OpenGL: renderer: llvmpipe (LLVM 15.0.6 256 bits)
    v: 4.5 Mesa 22.2.5

```

@ActionParsnip: I think you're right. I looked at Xorg logs and found this:

```

:$ cat /var/log/Xorg.0.log | grep \(EE\)
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   717.958] (EE) open /dev/dri/card0: No such file or directory
[   717.958] (EE) open /dev/dri/card0: No such file or directory
[   717.959] (EE) Unable to find a valid framebuffer device
[   717.959] (EE) open /dev/fb0: No such file or directory
[   717.959] (EE) Screen 0 deleted because of no matching config section.
[   717.959] (EE) Screen 0 deleted because of no matching config section.
[   717.959] (EE) Screen 0 deleted because of no matching config section.

```

So I reinstalled xserver-xorg-video-radeon and xserver-xorg-core but it didn't work either.

```

:$ sudo apt reinstall xserver-xorg-video-radeon xserver-xorg-core
:$ sudo dpkg-reconfigure xserver-xorg

```

Sadly, I still get the same errors on xorg log:

```

(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    69.058] (EE) open /dev/dri/card0: No such file or directory
[    69.058] (EE) open /dev/dri/card0: No such file or directory
[    69.060] (EE) Unable to find a valid framebuffer device
[    69.060] (EE) open /dev/fb0: No such file or directory
[    69.061] (EE) Screen 0 deleted because of no matching config section.
[    69.061] (EE) Screen 0 deleted because of no matching config section.
[    69.061] (EE) Screen 0 deleted because of no matching config section.

```

I now tried adding this PPA rep and it worked a couple times, is not working anymore:

```

:$ sudo add-apt-repository ppa:oibaf/graphics-drivers

:$ sudo apt update && sudo apt -y upgrade

```

Any ideas are welcome.

---

