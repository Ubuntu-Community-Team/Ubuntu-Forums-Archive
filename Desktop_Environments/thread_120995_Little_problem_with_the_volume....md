---
title: "Little problem with the volume..."
date: 2006-01-24
forum: Desktop Environments
---

### Post by Tiede on 2006-01-24
Hi. No, this is not to say that sound does not work in Ubuntu, my hardware is detected quite well. I didn't have to lift a finger to get sound working this time ;)
I do have a curiously interesting problem, though: My volume channels are messed up. The main slider doesn't change nothing at all, the Headphone and PCM sliders are the ones that actually work. As a result, the 2 shortcuts that control the volume do not work. I can see the slider going down/up, but nothing happens unless I open the main volume control and slide the Headphone or the PCM channels until I reach the desired setting. This is not a big problem but it can get a bit annoying at times.
Has anyone experienced the same thing and/or know a fix to it?
Thanks in advance for your answers, guys.

PS: Some specs cause those never hurt.
I am running Breezy on a Acer 3003WLCi laptop and here is my lshw -short
```
marc@Tuxed:~$ sudo lshw -short
H/W path             Device    Class          Description
=========================================================
                               system         Aspire 3000
/0                             bus            Lugano M
/0/0                           memory         BIOS
/0/4                           processor      Mobile AMD Sempron(tm) Processor 3000+
/0/4/8                         memory         L1 cache
/0/4/9                         memory         L2 cache
/0/10                          memory         System Memory
/0/1                           memory
/0/1/0                         memory         DIMM DDR Synchronous
/0/2                           memory
/0/2/0                         memory         DIMM DDR Synchronous
/0/3                           memory
/0/5                           memory
/0/e0000000                    bridge         760/M760 Host
/0/e0000000/1                  bridge         SG86C202
/0/e0000000/1/0                display        661/741/760 PCI/AGP VGA Display Adapter
/0/e0000000/2                  bridge         SiS963 [MuTIOL Media IO]
/0/e0000000/2.1                bus            SiS961/2 SMBus Controller
/0/e0000000/2.5                storage        5513 [IDE]
/0/e0000000/2.5/0    ide0      bus            IDE Channel 0
/0/e0000000/2.5/0/0  /dev/hda  disk           WDC WD600UE-22HCT0
/0/e0000000/2.5/1    ide1      bus            IDE Channel 1
/0/e0000000/2.5/1/0  /dev/hdc  disk           HL-DT-STCD-RW/DVD DRIVE GCC-4244N
/0/e0000000/2.6                communication  AC'97 Modem Controller
/0/e0000000/2.7                multimedia     Sound Controller
/0/e0000000/3                  bus            USB 1.0 Controller
/0/e0000000/3/1      usb1      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller
/0/e0000000/3.1                bus            USB 1.0 Controller
/0/e0000000/3.1/1    usb2      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
/0/e0000000/3.2                bus            USB 2.0 Controller
/0/e0000000/3.2/1    usb3      bus            Silicon Integrated Systems [SiS] USB 2.0 Controller
/0/e0000000/4        eth0      network        SiS900 PCI Fast Ethernet
/0/e0000000/6                  bridge         PCI1410 PC card Cardbus Controller
/0/e0000000/b        wlan0     network        Broadcom Corporation
/0/100                         bridge         K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/101                         bridge         K8 [Athlon64/Opteron] Address Map
/0/102                         bridge         K8 [Athlon64/Opteron] DRAM Controller
/0/103                         bridge         K8 [Athlon64/Opteron] Miscellaneous Control
marc@Tuxed:~$

```

---

### Post by dogson on 2006-01-24
Set PCM to below 75% and change the Master line to Headphone in the gnome volume applet (right click and settings) select Headphone. thats how i did it

---

### Post by Tiede on 2006-01-25
I right-clicked on the gnome volume applet and chose settings. However, even though Headphones is highlighted, it still keeps on adjusting the main volume level...  Does this fix require a restart?
EDIT: I misunderstood you. what you suggested makes the + and - signs actually control the volume, which is half of what I wanted.
I also have two shorcuts on my keyboard that can control the volume, but when I use the buttons, the slider that actually moves is still the main slider.
Thanks for putting me halfway there though :)

---

### Post by stream303 on 2006-01-25
> Set PCM to below 75% and change the Master line to Headphone in the gnome volume applet (right click and settings) select Headphone. thats how i did it

**THANK YOU!!!**  Me and my old Dell Optiplex GX150 are very grateful!

---

### Post by Tiede on 2006-01-26
Am I to believe no one knows how to switch two channels or reconfigure the volume-control so I can have the shortcuts (assigned by ubuntu itself) do soemthing else than slide a cute bar accross my desktop?

---

### Post by Tiede on 2006-01-30
dropping in to say that upgrading to dapper seem to fix the problem. It removed the headphones channel completely and main controld the sound perfectly.

---

