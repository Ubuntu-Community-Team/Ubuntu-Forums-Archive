---
title: "Display problems"
date: 2006-12-07
forum: Desktop Environments
---

### Post by JoeS on 2006-12-07
Use Linux: Ubuntu Breezy Badger

These are the hardware components I want to use:

Computer:
Dell Optiplex GX100
Bios Version: A10
Intel Corp VGA Adapter IRQ9

I found this in the Xorg.config file:
> 
Section "Device"
        Identifier      "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:1:0"
EndSection


Monitor:
Hewlett Packard: Pavilion M50
Model No. D5258A
Product No. D525-60010

The monitor works fine on another computer.  It also works to boot it up on this computer:  Shows the printout of what is happening.  When it has finished booting all I get is a black screen and text: "Display settings correct?" , which flashes once.

Can someone help to resolve this problem.
Thanks.

---

### Post by taurus on 2006-12-07
Maybe the refreshing rates are wrong!!!  What happens if you reconfigure your X again by booting into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by JoeS on 2006-12-10
> **taurus said:**
> Maybe the refreshing rates are wrong!!!  What happens if you reconfigure your X again by booting into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

Thanks for your response.
The new xorg.conf file after running:
'dpkg-reconfigure -phigh xserver-xorg' is this:

> Section "Monitor"
[INDENT]Identifier     "PAVILION M50"[/INDENT]
[INDENT]Option         "DMPS"[/INDENT]
EndSection

In the old file there was also this part in the monitor section:
> [INDENT]HorizSync     28-64[/INDENT]
[INDENT]VertRefresh     43-75[/INDENT]
I added VertRefresh which didn't do anything. I added both and lost the display.

Can I edit the xorg.conf file to get a higher refresh rate.  At 1024 x 768 I can only get 60hz.

---

### Post by taurus on 2006-12-10
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by CatKiller on 2006-12-11
> **JoeS said:**
> In the old file there was also this part in the monitor section:
>     HorizSync 28-64

    VertRefresh 43-75
I added VertRefresh which didn't do anything. I added both and lost the display.

According to [this page]("http://www.shopping.com/xPF-Hewlett-Packard-HP-Pavilion-M50-15-in"), those values should be ```
    HorizSync 30-54
    VertRefresh 50-100
``` I don't know where you got your values from.

---

### Post by JoeS on 2006-12-18
> **CatKiller said:**
> According to [this page]("http://www.shopping.com/xPF-Hewlett-Packard-HP-Pavilion-M50-15-in"), those values should be ```
    HorizSync 30-54
    VertRefresh 50-100
``` I don't know where you got your values from.

I added > HorizSync 30-54; VertRefresh 50-100 
This didn't change anything compared to leaving it out of the xorg.conf file.
If I change it to VertRefresh 70-100 it will only give me up to 800x600 resolution.
 
What is limiting the 1024x786 to 60hz resolution.  Is it the monitor or video card or something else?

---

