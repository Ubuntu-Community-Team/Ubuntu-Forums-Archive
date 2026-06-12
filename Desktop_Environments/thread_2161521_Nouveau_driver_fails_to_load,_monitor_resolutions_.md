---
title: "Nouveau driver fails to load, monitor resolutions limited"
date: 2013-07-11
forum: Desktop Environments
---

### Post by edwards2013 on 2013-07-11
Greetings from a first time Linux installer.

I recently decided to try running an old piece of hardware using Linux, and after research and some testing I settled on xubuntu 12.04.2. The system is a Gateway 486 machine running an nvidia Riva TNT. For the most part, this is actually working well and I am happy with my choices thus far. Now for the issue. The screen resolution is limited to 1024x768 or lower, which although somewhat useable for what I am doing with this machine, is a bit annoying when trying to work with just about any website. The card and monitor (Samsung SyncMaster 204bw) are capable of more, although I would be happy with 1280x1024 if I can get it there.

I first tried installing the nvidia driver 71.86.15 from their website, and that led to all sorts of new issues but no improvement in resolution. Next came a variety of attempts at an xorg.conf file using modelines and setup suggestions that seemed to do more harm than good. I backed out of that, but I couldn't seem to completely clear the nvidia driver's influence, so I reinstalled xubuntu and messed up my Grub setup. I fixed that problem, so I am running again but still at a limited res. I did a lot more research this time and after digging through many posts and logs, I can see in the Xorg.0.log that the nouveau kernel fails to load and the system defaults to vesa. Further digging with modprobe shows errors inserting wmi, mxm_wmi, i2c_algo_bit, drm, drm_kms_helper, ttm, and the Fatal error inserting nouveau. Per the nouveau.freedesktop.org/wiki/troubleshooting information, running ldd indicates:

desktop:~/ sudo ldd /usr/lib/xorg/modules/drivers/nouveau_drv.so
    linux-gate.so.1 => (0x0096d000)
    libdrm_nouveau.so.1 => /usr/lib/i386-linux-gnu/libdrm_nouveau.so.1 (0x00961000)
    libudev.so.0 => /lib/i386-linux-gnu/libudev.so.0 (0x00c50000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x0014d000)
    libdrm.so.2 => /usr/lib/i386-linux-gnu/libdrm.so.2 (0x00a05000)
    librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0x0043c000)
    /lib/ld-linux.so.2 (0x00ae4000)
    libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0x00e69000)

which I believe shows a difference between the libdrm_nouveau.so.1 and libdrm.so.2, although I am not certain if this matters nor can I discern how to correct it as I did not compile the kernel. Additional searches thus far have failed to show the way out of this (or at least in a method that I can understand). I have log files that I can upload if that helps, but figured I would start this way.

My question then is can this ever work on the setup I have (i.e., 1280x1024 resolution), and if so what would be my next steps to get there. I do like the operation of xubuntu, and the education thus far has been quite a mind stretch.

Many thanks in advance.

Edwards

---

### Post by BreezyBrooke on 2013-07-11
That computer is WAY TO OLD FOR ANYTHING... if it really is a Intel 80486 in there, you are runing a miracle machine. Thing is, not even the open source driver supports that card anymore, and how much ram do you have?!?! Can't be more than 64MB, which is too low for even Xubuntu!!!


Are you being legit here?

---

### Post by edwards2013 on 2013-07-11
Quite legit. The setup is 640 MB of SDRAM, and as I indicated runs well for the most part. I am not trying to do any 3D work or video playback - merely a separate work and browsing machine from my other equipment.

According to nouveau the Riva TNT is still supported, at least in the documentation I have seen and in the Xorg.0.log file:

[    49.923] (II) Failed to load module "fbdev" (already loaded, 0)
[    49.923] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    49.923] (II) NOUVEAU driver for NVIDIA chipset families :
[    49.923]     RIVA TNT        (NV04)
[    49.923]     RIVA TNT2       (NV05)
[    49.924]     GeForce 256     (NV10)
[    49.924]     GeForce 2       (NV11, NV15)
[    49.924]     GeForce 4MX     (NV17, NV18)
[    49.925]     GeForce 3       (NV20)
[    49.925]     GeForce 4Ti     (NV25, NV28)
[    49.925]     GeForce FX      (NV3x)
[    49.926]     GeForce 6       (NV4x)
[    49.926]     GeForce 7       (G7x)
[    49.926]     GeForce 8       (G8x)
[    49.927]     GeForce GTX 200 (NVA0)
[    49.927]     GeForce GTX 400 (NVC0)

Thanks anyway.

---

### Post by jp734 on 2013-07-11
Sometimes, monitor's horizontal and vertical refresh rates need to specified on xorg.conf file for it to work on max resolution. 

HorizSync 30-80
VertRefesh 50-85

Above is an example of what is needed to be added on your Section "Monitor". Find out what yours is and change the value.

---

### Post by VinDSL on 2013-07-11
> **edwards2013 said:**
> According to nouveau the Riva TNT is still supported, at least in the documentation I have seen and in the Xorg.0.log file [...]
That's my understanding, too, from reading this... 

[http://ubuntuforums.org/showthread.php?t=1429243&p=8968779&viewfull=1#post8968779](http://ubuntuforums.org/showthread.php?t=1429243&p=8968779&viewfull=1#post8968779)

---

### Post by edwards2013 on 2013-07-12
Thank you for the reply, but I have tried that already to no avail. As a further test this evening, I created a new xorg.conf file in the attempt to force vesa to utilize the 1280x1024 setting. The Xorg log shows it just being ignored and loading the 1024x768 again. I am still trying to find some combination of settings to achieve a higher resolution, and I did more research into a custom install of nouveau in the hope that it will work but the information available is beyond my skill level right now. If I could get a step-by-step of how to make the libdrm versions match it might be helpful, but then again I keep running into dead ends. I'll keep digging and hope a solution appears.

Edwards

PS - sorry, I'm new to this. This reply was to the suggestion regarding the refresh rates.

---

### Post by VinDSL on 2013-07-12
First thing I would do is make sure nouveau isn't blacklisted.

Open a terminal window, and...

```
cat /etc/modprobe.d/* | egrep 'blacklist nouveau'
```

This will check all the files in the modprobe.d folder.

Here's the output on my machine...

```
vindsl@Zuul:~$ cat /etc/modprobe.d/* | egrep 'blacklist nouveau'
blacklist nouveau
blacklist nouveau
vindsl@Zuul:~$
```

Nouveau is blacklisted in two different places. Nouveau drivers won't work, unless I comment/delete those lines.

Secondly, I wouldn't be running a xorg.conf file.  All that will do is jack things up... ;)

---

### Post by edwards2013 on 2013-07-12
Thanks for the reply VinDSL. I have checked this, and to be sure I ran it again per your instructions. Nothing comes up using " | egrep 'blacklist nouveau' ". To be sure, I ran the command with just 'blacklist' and got the information in the attached text doc.

I also have a few days of jacked up results due to the xorg.conf file (including a couple of black screen boots due to mistakes in my entries). I'm just testing to try to get anything to work here, and hopefully once I find a good configuration I can get back to a more streamlined setup. Here is the xorg.conf I just ran, although it did nothing:

[SIZE=1]Section "Device"
    Identifier    "Card0"
    VendorName    "NVIDIA Corporation"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
    Option        "ModeValidation" "AllowNonEdidModes"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "Samsung"
    Modelname    "SyncMaster 204bw"
    HorizSync    30-81
    VertRefresh    56-75
    Modeline    "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  +hsync +vsync
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Card0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection        "Display"
        Viewport    0 0
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection[/SIZE]

I tried to keep it as simple as possible to avoid making other things worse. It seems that there is no good combination of supported resolutions common to the monitor, the nvidia card, and vesa other than 1024x768, 800x600, and 640x480.

The somewhat good news is that the EDID information is being read by the system as evidenced in the Xorg log (also attached with info from a non xorg.conf boot, but some sections edited to meet upload size limit). The bad is that nouveau seems to load but ends up not doing so, as also evidenced by this modprobe result:

-desktop:~/ sudo modprobe nouveau
WARNING: Error inserting wmi (/lib/modules/3.2.0-49-generic/kernel/drivers/platform/x86/wmi.ko): No such device
WARNING: Error inserting mxm_wmi (/lib/modules/3.2.0-49-generic/kernel/drivers/platform/x86/mxm-wmi.ko): No such device
WARNING: Error inserting i2c_algo_bit (/lib/modules/3.2.0-49-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko): No such device
WARNING: Error inserting drm (/lib/modules/3.2.0-49-generic/kernel/drivers/gpu/drm/drm.ko): No such device
WARNING: Error inserting drm_kms_helper (/lib/modules/3.2.0-49-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko): No such device
WARNING: Error inserting ttm (/lib/modules/3.2.0-49-generic/kernel/drivers/gpu/drm/ttm/ttm.ko): No such device
FATAL: Error inserting nouveau (/lib/modules/3.2.0-49-generic/kernel/drivers/gpu/drm/mouveau/nouveau.ko): No such device

Also, please reference the ldd results from last night's post.

I understand that I'm pushing some limits with the old equipment, but as I keep reading and researching it seems that the answer is out there but just out of my reach. Other than the resolution, things are working great.

Thanks for reading.

Edwards

---

### Post by jp734 on 2013-07-12
Are you sure you have Riva TNT? Maybe you have Riva 128 which is the last model before Riva TNT?  Also, try 16 bit color depth instead of 24? Just throwing some things to think about.

---

### Post by edwards2013 on 2013-07-12
> **jp734 said:**
> Are you sure you have Riva TNT? Maybe you have Riva 128 which is the last model before Riva TNT?

Well, that's the $64k question. I assumed such based on Windows Device Manager and Display Properties indicating it is an nvidia riva tnt nv4, and Everest output this:

[SIZE=1]--------[ EVEREST Home Edition (c) 2003-2005 Lavalys, Inc. ]------------------------------------------------------------

    Version                                           EVEREST v2.20.405
    Homepage                                          [http://www.lavalys.com/](http://www.lavalys.com/)
    Report Type                                       Report Wizard
    Computer                                          -DESKTOP
    Generator                                         
    Operating System                                  Microsoft Windows 2000 Professional 5.0.2195 (Win2000 Retail)
    Date                                              2013-07-01
    Time                                              20:23


--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Operating System                                  Microsoft Windows 2000 Professional
      OS Service Pack                                   Service Pack 4
      DirectX                                           4.09.00.0904 (DirectX 9.0c)
      Computer Name                                     -DESKTOP
      User Name                                         

    Motherboard:
      CPU Type                                          Intel Pentium III, 450 MHz (4.5 x 100)
      Motherboard Name                                  Intel Warm Springs WS440BX  (1 ISA, 5 PCI, 1 AGP, 3 DIMM)
      Motherboard Chipset                               Intel 82440BX
      System Memory                                     640 MB  (SDRAM)
      BIOS Type                                         Phoenix (04/22/99)
      Communication Port                                Communications Port (COM1)
      Communication Port                                Communications Port (COM3)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     NVidia Riva TNT  (16 MB)
      3D Accelerator                                    nVIDIA RIVA TNT
      Monitor                                           Plug and Play Monitor [NoDB]  (HVJP916972) [/SIZE]

But I opened up the case this morning just to be sure. The primary chip has the heat sink glued to it and I do not currently have the stuff to replace that, so I cannot see the information on top. The card itself appears very similar to photos on line when searching for nvidia riva tnt, so I'm reasonably certain that this is the case. I'll drop by Fry's on the way home tonight and get some of the heat sink glue so I can verify the chip information.

I'll also try reducing the color depth.

Thanks for your reply

Edwards

---

### Post by VinDSL on 2013-07-12
> **edwards2013 said:**
> Everest output [...]
    Motherboard:
      CPU Type                                          Intel Pentium III, 450 MHz (4.5 x 100)
      Motherboard Name                                  Intel Warm Springs WS440BX  (1 ISA, 5 PCI, 1 AGP, 3 DIMM)
      Motherboard Chipset                               Intel 82440BX
      System Memory                                     640 MB  (SDRAM)
      BIOS Type                                         Phoenix (04/22/99)
      Communication Port                                Communications Port (COM1)
      Communication Port                                Communications Port (COM3)
      Communication Port                                ECP Printer Port (LPT1)
Aha!  P3.  I'm running a P4EE (see sig).  Just saying...

The oldest computer I have, that will run a modern Linux distro, with beautiful graphics, et cetera, is an eMachine eTower (circa 1998 / WinME).  A friend donated it to me -- 667MHz Celeron, 192MB RAM, Intel GPU, blah, blah, blah.  Soooo, it is doable, but...

The only distro I could find, that would boot from the HD (and, I tried many), was Macpup Opera 2.0 ([a Puppy Linux fork]("http://macpup.org/opera2.php")).  The eMachine was an extreme example of mostly proprietary hardware, but [Puppy Linux]("http://puppylinux.org/") et al. works just fine, generally speaking, on most ancient iron.

I also have a Celeron-powered netbook, bootable USB sticks, and so forth that require a light OS (otherwise they are intolerably slow).  On modern mobile devices (laptop, netbook, USB sticks) I run Peppermint OS ([an Ubuntu fork]("http://peppermintos.com/")).  It flies like the wind, on modest hardware.

If it was me, I would be looking for a modern Linux distro, that was designed around an older kernel (intentionally older, for older hardware).  That's what I recommend, and what I do.

As time goes on, older hardware support starts getting pulled from the latest Linux kernel(s).  They do that mostly to keep the size down.  Kernels are constantly changing -- support for newer devices is added, and support for older devices is removed.  P3/i386 support [has totally been removed]("http://news.softpedia.com/news/Linux-Kernel-3-8-Says-Goodbye-to-i386-314293.shtml") on the most recent kernels.  I'm running Linux 3.10 successfully on this P4/i686 box, but my time is coming, too.  The distros I mentioned above (and personally run myself) will continue to support i386 machines, via older kernels, for some time to come.  It's their 'bag', you know?  :)

Anyway, I would burn a couple of bootable CD's with Macpup Opera 2.0, and Peppermint OS -- boot them up, see how they run (I think you'll be amazed at the difference in performance).  If everything goes well, install one_or_the_other on your HD, and call it a day.

Otherwise, you might get away with downgrading your current OS, and once you get it working again, start pinning packages to protect them from being upgraded in the future.

---

### Post by edwards2013 on 2013-07-12
Well, I figured that I might run into some dead ends on this project so it's not too surprising. The interesting part is that TinyCore running with XVesa provides full display resolution support, albeit with a more limited desktop environment. I did have Puppy Linux on the short list but have not tried it yet. Xubuntu came up in searches and runs fine for what I am doing, which does not require a graphics heavy environment, so I decided to go with that distro. I know that the age of the equipment is at the edge of being unsupported, end-of-life gear, but the part that keeps me going is that it runs well and all the documentation says it should work. I am also hoping to have some reasonable level of supported OS to insure a modicum of security while exposed to the web. I have not done a lot of customization of the install yet, so mistakes made now are easily cleared with a reinstall (especially now that I understand Grub better). I'll probably try some tweaking of Nouveau once I wrap my head around how to do those installs and activations - I'm still digging through the freedesktop.org site and documentation which is not really geared toward noobs like me.

Thanks for all of the assistance and suggestions. I'll leave the thread open for another day or so in the hopes that someone will take a look over the weekend and offer up a new idea or two. If I come up with something that happens to work I'll also post the results.

Edwards

---

### Post by jp734 on 2013-07-14
If thinking about going for a different distro, I recommend Slitaz. A very lightweight distro for old computers. They 3.0 and 4.0 stable versions. Installed 3.0 on p3 600mhz and the pc boots in 15 seconds.

---

### Post by edwards2013 on 2013-07-14
Thanks for the suggestion jp734. I have looked at Slitaz, but like Puppy I have not loaded either yet. I'll dig a bit further to see if they support a video driver other than nouveau or vesa, as the problem is related to display resolution rather than OS speed and operability. Xubuntu runs fine and does everything I try as quickly as I need it to, but the display is limited to 1024x768. I erroneously posted earlier that Tiny Core and Xvesa allowed a better display, but that was based on a visual improvement from an even lower (800x600) starting point change to 1024x768. I am in the process of trying to follow the compiling instructions on the nouveau site to see if this makes any difference, but I have a bit to learn about make files and how that works. I'm not certain it will do anything to improve the situation, but it's a fun experiment and learning process. I'll post a procedure (if I can determine one) for others who may want to undertake reviving very old hardware for the fun of it.

Thanks again all.

Edwards

---

