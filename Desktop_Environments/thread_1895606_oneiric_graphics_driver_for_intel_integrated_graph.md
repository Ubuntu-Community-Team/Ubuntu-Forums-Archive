---
title: "oneiric: graphics driver for intel integrated graphics?"
date: 2011-12-15
forum: Desktop Environments
---

### Post by jtheuer on 2011-12-15
Hi,

In the last release I was able to use xrandr to set up my resolution and (external) screens. Since I upgraded to oneiric it seems that X is only using the VESA driver and does not recognize external screens or support randr.

Here is my setup:

```

# lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

The X logfile says:
```

(...)
[     7.669] (II) LoadModule: "intel"
[     7.671] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     7.676] (II) Module intel: vendor="X.Org Foundation"
[     7.676]    compiled for 1.10.4, module version = 2.15.901
[     7.676]    Module class: X.Org Video Driver
[     7.676]    ABI class: X.Org Video Driver, version 10.0
[     7.676] (II) LoadModule: "vesa"
[     7.676] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.678] (II) Module vesa: vendor="X.Org Foundation"
[     7.678]    compiled for 1.10.2, module version = 2.3.0
[     7.678]    Module class: X.Org Video Driver
[     7.678]    ABI class: X.Org Video Driver, version 10.0
[     7.678] (II) LoadModule: "fbdev"
[     7.678] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.679] (II) Module fbdev: vendor="X.Org Foundation"
[     7.679]    compiled for 1.10.0, module version = 0.4.2
[     7.679]    ABI class: X.Org Video Driver, version 10.0
[     7.680] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
        Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
        Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
        Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
        Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
        Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[     7.680] (II) VESA: driver for VESA chipsets: vesa
[     7.680] (II) FBDEV: driver for framebuffer: fbdev
[     7.680] (++) using VT number 7
[     7.682] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.682] (WW) Falling back to old probe method for fbdev
[     7.682] (II) Loading sub module "fbdevhw"
[     7.682] (II) LoadModule: "fbdevhw"
[     9.444] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.477] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.477]    compiled for 1.10.4, module version = 0.0.2
[     9.477]    ABI class: X.Org Video Driver, version 10.0
[     9.477] (II) Loading sub module "vbe"
[     9.477] (II) LoadModule: "vbe"
[     9.477] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.484] (II) Module vbe: vendor="X.Org Foundation"
[     9.485]    compiled for 1.10.4, module version = 1.1.0
[     9.485]    ABI class: X.Org Video Driver, version 10.0
[     9.485] (II) Loading sub module "int10"
[     9.485] (II) LoadModule: "int10"
[     9.485] (II) Loading /usr/lib/xorg/modules/libint10.so
[     9.493] (II) Module int10: vendor="X.Org Foundation"
[     9.493]    compiled for 1.10.4, module version = 1.0.0
[     9.493]    ABI class: X.Org Video Driver, version 10.0
[     9.493] (II) VESA(0): initializing int10
[     9.494] (II) VESA(0): Bad V_BIOS checksum
[     9.494] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[     9.494] (II) VESA(0): VESA BIOS detected
[     9.494] (II) VESA(0): VESA VBE Version 3.0
[     9.494] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[     9.494] (II) VESA(0): VESA VBE OEM: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
[     9.494] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[     9.494] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[     9.494] (II) VESA(0): VESA VBE OEM Product: Intel(r)Cantiga Graphics Controller
[     9.494] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[     9.502] (II) VESA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     9.503] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[     9.503] (==) VESA(0): RGB weight 888
[     9.503] (==) VESA(0): Default visual is TrueColor
[     9.503] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[     9.503] (II) Loading sub module "ddc"
[     9.503] (II) LoadModule: "ddc"
[     9.503] (II) Module "ddc" already built-in
[     9.503] (II) VESA(0): VESA VBE DDC supported
[     9.503] (II) VESA(0): VESA VBE DDC Level 2
[     9.503] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[     9.515] (II) VESA(0): VESA VBE DDC read successfully
[     9.526] (II) VESA(0): Manufacturer: LEN  Model: 4010  Serial#: 0
[     9.526] (II) VESA(0): Year: 2008  Week: 34
[     9.526] (II) VESA(0): EDID Version: 1.3
[     9.526] (II) VESA(0): Digital Display Input
[     9.526] (II) VESA(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[     9.526] (II) VESA(0): Gamma: 2.20
[     9.526] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[     9.526] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     9.526] (II) VESA(0): First detailed timing is preferred mode
[     9.526] (II) VESA(0): redX: 0.577 redY: 0.338   greenX: 0.310 greenY: 0.563
[     9.526] (II) VESA(0): blueX: 0.158 blueY: 0.157   whiteX: 0.313 whiteY: 0.329
[     9.526] (II) VESA(0): Manufacturer's mask: 0
[     9.526] (II) VESA(0): Supported detailed timing:
[     9.526] (II) VESA(0): clock: 75.3 MHz   Image Size:  261 x 163 mm
[     9.526] (II) VESA(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1512 h_border: 0
[     9.526] (II) VESA(0): v_active: 800  v_sync: 802  v_sync_end 804 v_blanking: 830 v_border: 0
[     9.526] (II) VESA(0): Supported detailed timing:
[     9.526] (II) VESA(0): clock: 59.3 MHz   Image Size:  261 x 163 mm
[     9.526] (II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[     9.526] (II) VESA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[     9.526] (II) VESA(0): Unknown vendor-specific block f

(...)

```

I don't have any xorg config files (anymore).

How do I get back my original intel driver and randr support?

Thanks,

Jan

---

### Post by thaelim on 2011-12-16
My laptop has a very similar platform to yours. Your log looks identical to mine up to a point. I don't see any errors before that point that give indications as to why the intel driver isn't loading. However the next thing I see in my log is a bunch of message from drm. So I would start by checking that all the drm stuff is properly installed:

```
sudo apt-get install --reinstall libdrm-intel1 libdrm2
```

---

