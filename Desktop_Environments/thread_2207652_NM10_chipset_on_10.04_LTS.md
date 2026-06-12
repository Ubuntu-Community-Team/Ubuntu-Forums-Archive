---
title: "NM10 chipset on 10.04 LTS"
date: 2014-02-24
forum: Desktop Environments
---

### Post by darkog on 2014-02-24
Hi, I am trying to get an Intel Atom NM10 chipset  based desktop to display in full 1920x1080 resolution on a Ubuntu 10.04.4 LTS. Does anyone know what driver they were able to get this to work with? 


```
11: None 03.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: 4zLr.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 6.54.1 "Intel(R) Atom(TM) CPU D2550   @ 1.86GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,nx,constant_tsc,arch_perfmon,pebs,bts,nonstop_tsc,aperfmperf,pni,dtes64,monitor,ds_cpl,tm2,ssse3,xtpr,pdcm,movbe,lahf_lm,arat
  Clock: 1862 MHz
  BogoMips: 3724.84
  Cache: 512 kb
  Units/Processor: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _Znp.TQ4hKBZ9in3
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0be2
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x84a9
  Revision: 0x0b
  Memory Range: 0xdfc00000-0xdfcfffff (rw,non-prefetchable)
  I/O Ports: 0xf0d0-0xf0d7 (rw)
  IRQ: 11 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000BE2sv00001043sd000084A9bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 1b.0: 0403 Audio device
  [Created at pci.318]
  Unique ID: u1Nb.MjtTeuzQj91
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801G (ICH7 Family) High Definition Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27d8 "82801G (ICH7 Family) High Definition Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x84f5
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdff00000-0xdff03fff (rw,non-prefetchable)
  IRQ: 22 (9911 events)
  Module Alias: "pci:v00008086d000027D8sv00001043sd000084F5bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```


```

(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Video Driver, version 6.0
(II) VESA(0): initializing int10
(II) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(R)XX Graphics Chipset Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(R)XX Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: a016  Serial#: 826626643
(II) VESA(0): Year: 2006  Week: 35
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
(II) VESA(0): Max Image Size [cm]: horiz.: 52  vert.: 33
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) VESA(0): Supported established timings:

```

---

### Post by darkog on 2014-02-25
any ideas? anyone? I am not sure if I am asking a question that has been asked many times or asking a question which is not possible. Given that we are using a LTS supported version -- does that not mean there is LTS support for such things?

---

### Post by Yellow Pasque on 2014-02-25
Ubuntu 10.04 is unsupported/EOL. You need a newer kernel to get a non-generic driver that will allow 1920x1080.

---

### Post by darkog on 2014-02-26
> **Temüjin said:**
> Ubuntu 10.04 is unsupported/EOL. You need a newer kernel to get a non-generic driver that will allow 1920x1080.

Thanks. I am using the 10.04 LTS server edition. According to this its not EOL until mid 2015.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Is there a way to get the graphics drivers which come with the newer kernel and inject them into 2.6.32?

---

### Post by open2reason on 2014-02-26
Could you load and run a live 12.04.4lts cd and then note what drivers it selects for you?
You could then search them out and then  if at all possible set about amending your system.

---

### Post by mörgæs on 2014-02-26
Since you mention a resolution of 1920x1080 you are runnning the desktop version which is unsupported.

There have been a lot of improvements for the Atoms in the latest releases so I suggest a clean install of 13.10.

---

### Post by darkog on 2014-03-04
> **mörgæs said:**
> Since you mention a resolution of 1920x1080 you are runnning the desktop version which is unsupported.

No. It's still the server edition. No special new repositories have been added to apt sources. Once I finished installing the OS and patching it, I ran "sudo aptitude install --without-recommends ubuntu-desktop" on the server edition to install Gnome. What are you saying? Once you install Gnome from the server repo it stops being a server edition and does not qualify for LTS support coverage?

> **mörgæs said:**
> There have been a lot of improvements for the Atoms in the latest releases so I suggest a clean install of 13.10.

If I could do that I would, but the issue is I am installing a python based client which is only supported on 10.04 LTS. I realize that this is pointing to directing questions to the developers of the other application but, Ubuntu is the one who is claiming they offer LTS support well into next year --  not the developers of the other application. So here I am, I have new hardware and am coming to Ubuntu asking to get LTS support on 10.x to try to get it working properly. The reply of, "just go get the latest version" doesn't sound like Long Term Support to me.

---

### Post by darkog on 2014-03-04
> **open2reason said:**
> Could you load and run a live 12.04.4lts cd and then note what drivers it selects for you?
You could then search them out and then  if at all possible set about amending your system.

I tried that too. It grabs a driver which is in the kernel I think.

---

### Post by mörgæs on 2014-03-04
> **darkog said:**
> Once you install Gnome from the server repo it stops being a server edition and does not qualify for LTS support coverage?

Correct. In fact, once you install any desktop environment you will be supported according to the conditions of said environment, that is three years for Gnome.

---

### Post by Yellow Pasque on 2014-03-04
> # Lucid source packages not in this list are unsupported starting Apr 29, 2013
[http://bazaar.launchpad.net/~ubuntu-security/ubuntu-cve-tracker/master/view/head:/lucid-supported.txt](http://bazaar.launchpad.net/~ubuntu-security/ubuntu-cve-tracker/master/view/head:/lucid-supported.txt)

---

### Post by grahammechanical on 2014-03-04
I do not think that the length of support is relevant. It is missing the point. Is there a video driver, open source or proprietary, that works with the 10.04 Linux kernel and the 10.04 Xserver to give the screen resolution that the OP requires?

Other questions. Was such a video driver available for 10.04 desktop? Did Nouveau give a 1920x1080 screen resolution back in 2004?

---

### Post by Yellow Pasque on 2014-03-04
> **grahammechanical said:**
>  Is there a video driver, open source or proprietary, that works with the 10.04 Linux kernel and the 10.04 Xserver to give the screen resolution that the OP requires?
No.

> Did Nouveau give a 1920x1080 screen resolution back in 2004?
This is an intel cedarview chip. I'm not sure why you're talking about nouveau...

---

### Post by darkog on 2014-03-09
> **mörgæs said:**
> Correct. In fact, once you install any desktop environment you will be supported according to the conditions of said environment, that is three years for Gnome.

> **Temüjin said:**
> [http://bazaar.launchpad.net/~ubuntu-security/ubuntu-cve-tracker/master/view/head:/lucid-supported.txt](http://bazaar.launchpad.net/~ubuntu-security/ubuntu-cve-tracker/master/view/head:/lucid-supported.txt)

Thanks to both of you. I didn't know these facts regarding LTS support. I was always under the impression that as long as you installed a server edition and kept to the packages in the official repo for that server edition you wee covered. 

I am going to guess there is no simple way to inject a driver from a new kernel into an order kernel?

---

### Post by Yellow Pasque on 2014-03-09
> **darkog said:**
> I am going to guess there is no simple way to inject a driver from a new kernel into an order kernel?

No (especially when said driver is closed source...).

---

### Post by mörgæs on 2014-03-10
Even if it were, why would you stick to four years old software? 
Time to see what the new releases have to offer.

---

