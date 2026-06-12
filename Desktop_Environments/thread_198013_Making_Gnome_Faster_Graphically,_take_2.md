---
title: "Making Gnome Faster Graphically, take 2"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Patrick-Ruff on 2006-06-16
hey all, this is the second time I've posted this since the last time there was really no useful answers.  I have my graphics card working perfectly, its definately not a lack of power as far as the video card goes.

heres my exact system specs
1.6GHz Pentium M 2MB L2 Cache
512MB DDR2 RAM
64MB ATI's Mobility Radeon X300 PCI Express (dedicated onboard memory)
my page file is default. 1.4GB

when I open up menus on the top bar for example, System -> Administration,
the icons take a quarter second to load, every aspect of the desktop seems like its not actually using hardware accelleration. YES my video drivers are working perfectly, I can play games with very nice FPS. I'm not changing desktop systems, nor using window managers that change my system drastically. I don't want to sacrifice looks, thats the only reason I'm using gnome, it FINALLY looks good! dapper made it look GREAT :D. but is it possible that gnome isant using hardware accelleration? if so, can this be fixed? there must be some kind of system file that I can possibly edit to make it actually perform for me. I mean, its laggier then windows it seems, and I know that should NOT be the case here. Gnome seems to be an extremely flexable desktop environment so I would think you could manipulate the accelleration to make it 'actually' work.


please help me...

-Patrick

---

### Post by Lord Illidan on 2006-06-16
Is DMA enabled?

Run sudo hdparm /dev/hd* on your terminal and post output here.

---

### Post by Patrick-Ruff on 2006-06-16
I haven't the slightest idea waht DMA is, but heres the output of that command. my hard drives name is SDA btw.
```
patrick@eclypse:~$ sudo hdparm /dev/sd*

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4864/255/63, sectors = 78140160, start = 0

/dev/sda1:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4864/255/63, sectors = 75119877, start = 63

/dev/sda2:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4864/255/63, sectors = 2, start = 75119940

/dev/sda5:
 IO_support   =256 (???)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 4864/255/63, sectors = 3020157, start = 75120003

```

illidan does indeed rule :D, I've been playing warcraft 3 for 3 years lol.

---

### Post by ubuntu_demon on 2006-06-16
here are some general tips :
[http://www.ubuntuforums.org/showthread.php?t=190072](http://www.ubuntuforums.org/showthread.php?t=190072)

regarding disk speed ... let's measure it using :

$sudo hdparm -t /dev/sda

Here's information about dma : [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by Patrick-Ruff on 2006-06-16
wow, well this is insanely screwed up! it seems that the majority of the system files in Ubuntu recognise my hard drive as HDA!!! no bloody wonder I'm getting such horrid performance! my hard drive is named SDA not HDA, this is screwed up, is there any way I can possibly rename my hard drive to HDA? lol. I mean seriously, this is insanity...

---

### Post by 23meg on 2006-06-16
Is your drive mounted as /dev/hdXY or /dev/sdXY? A regular IDE drive will be hdXY whereas a SCSI or SATA one will be sdXY. Type```
df
```to find out. I highly doubt it will affect graphics performance in any case. > I mean, its laggier then windows it seems, and I know that should NOT be the case here.No, it's to be expected. X doesn't utilize hardware acceleration as efficiently as the Windows GUI at the moment and is thus slower in terms of 2D performance in most cases.

---

### Post by Patrick-Ruff on 2006-06-16
it seems to be using the SD range, I see no logical reason for it to be 4 times slower then the windows XP GUI.  do you? its using /dev/SDA1

---

### Post by 23meg on 2006-06-16
> it seems to be using the SD range,
That's normal if it's a SATA drive. Where is it listed as hda?
> I see no logical reason for it to be 4 times slower then the windows XP GUI. do you?
How much slower depends on your configuration and hardware, but generally speaking it will be slower in many operations. Is powernowd running? Post the output of ```
ps -e |grep powernowd
```

---

### Post by el3ktro on 2006-06-16
This has nothing to do with your harddisk. Gnome just uses a damn freaking slow window manager. Although it is still beta, I'd suggest you to at least try out Xgl, which uses OpenGL acceleration to draw the desktop - it's much faster!

Tom

---

### Post by Patrick-Ruff on 2006-06-16
yeah, I tried XGL and it kinda screwed up lol. I suppose I'll try it again :).

---

