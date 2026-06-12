---
title: "Help Please! Ubuntu 10.10 Intel HD Graphics"
date: 2010-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jnewing on 2010-12-16
So I have a latitude e6410 laptop running ubuntu 10.10 but the issue is with the Intel HD graphics card. ubuntu seems to only detect it being able to do one resolution! 

Help please and thank you.

---

### Post by sikander3786 on 2010-12-16
Go to Terminal under Applications > Accessories and post the output of these commands.

```
lspci | grep VGA
```

```
cat /etc/X11/xorg.conf
```

Note, capital 'X' for X11 ;-)

---

### Post by jnewing on 2010-12-16
lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

There is no /etc/X11/xorg.conf does not exist in ubuntu 10.10

---

### Post by sikander3786 on 2010-12-16
Switch to tty1 and try to reconfigure your graphics. Press Ctrl + Alt + F1 from your desktop and try this.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

```
sudo shutdown -r now
```

And see if that makes any difference now.

---

### Post by jnewing on 2010-12-16
no difference still only one resolution available :(

---

### Post by fjgaude on 2010-12-16
Okay, what does this show:

```
sudo lshw -c display
```

Likely your card is not claimed.

---

### Post by jnewing on 2010-12-16
lshw -c display
```

PCI (sysfs)  

SCSI                      
Framebuffer devices
  *-display        
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:70b0(size=8)
```

---

### Post by fjgaude on 2010-12-16
Looks correct... can't say what to check next. your board is recognized but the driver is not up-to-speed. Same on Intel and the kernel.

---

### Post by jnewing on 2010-12-16
> **fjgaude said:**
> Looks correct... can't say what to check next. your board is recognized but the driver is not up-to-speed. Same on Intel and the kernel.

:( damn I would really like to be able to do more than one resolution.

---

### Post by fjgaude on 2010-12-16
From what little I know of these things is the video driver doesn't recognize your monitor, the display screen in your computer. Maybe some one else will have an idea that solves your problem.

Help!

---

### Post by jnewing on 2010-12-16
> **fjgaude said:**
> From what little I know of these things is the video driver doesn't recognize your monitor, the display screen in your computer. Maybe some one else will have an idea that solves your problem.

Help!

Would there be any benefit to backing down version to like 9.x perhaps for more known solutions etc... or am I way off base there?

---

### Post by fjgaude on 2010-12-16
> **jnewing said:**
> Would there be any benefit to backing down version to like 9.x perhaps for more known solutions etc... or am I way off base there?

Can't say if that would help. Did you ever have a version of Linux that worked correctly with your laptop?

The newer versions of Ubuntu seem to have more and better drivers for hardware than earlier ones. From 10.04 which drops xorg.conf we have issues with not being able to change monitor modes. You could try 9.04 and seen if you can edit its xorg.conf file to fit your monitor. I think 9.10 was less of an upgrade than many wanted. I hope this helps.

---

### Post by jnewing on 2010-12-16
> **fjgaude said:**
> Can't say if that would help. Did you ever have a version of Linux that worked correctly with your laptop?

The newer versions of Ubuntu seem to have more and better drivers for hardware than earlier ones. From 10.04 which drops xorg.conf we have issues with not being able to change monitor modes. You could try 9.04 and seen if you can edit its xorg.conf file to fit your monitor. I think 9.10 was less of an upgrade than many wanted. I hope this helps.

I've never tried any other versions on this laptop (as this lappy is new to me) but I wouldn't be ad-versed to trying what version would you recommend.

---

### Post by fjgaude on 2010-12-16
Try 9.04 and if it works, fine! If not, come back here and show what the xorg.conf file is.

Good luck!

---

### Post by ivicks on 2010-12-16
I had kind of the same issue with my video card so I switched it to a generic vesa setting and that fixed my problems. I only use the computer for basic stuff so I didnt need any "HD" settings.

---

### Post by jnewing on 2010-12-16
> **ivicks said:**
> I had kind of the same issue with my video card so I switched it to a generic vesa setting and that fixed my problems. I only use the computer for basic stuff so I didnt need any "HD" settings.

How could I do this?

---

### Post by filleellif1987 on 2011-01-13
```
sudo nano /etc/X11/xorg.conf
```

Edit the line "Driver" in the "Device" section to vesa so it says:

```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

```

---

### Post by darkhelmetchris on 2011-01-14
> **jnewing said:**
> lshw -c display
```

...
...
       configuration: driver=i915 latency=0

```

Wow, I might use this little trick twice in one day...?

I have seen various problems when the video driver is detected as i915.  I'd like to suggest that you add this kernel parameter to your grub configuration and let me know if it helps you too:
```
i915.modeset=0
```

---

