---
title: "How to switch from nvidia to nouveau drivers on the CLI"
date: 2024-01-25
forum: Desktop Environments
---

### Post by actionmystique2 on 2024-01-25
**Environment**:
- Ubuntu 23.10 mantic
- ubuntu-desktop
- linux 6.6.0-14-generic
- lightdm
- NVIDIA & AMD GPUs

I installed Nvidia drivers with:
```
apt install nvidia-driver-535 linux-modules-nvidia-535-generic
```
I tried to enable them with:
```

prime-select nvidia

```[COLOR=#000000]
[/COLOR]which turned out to be a **huge mistake**.

On reboot, I stumbled on the infamous **oh no something has gone wrong** message with the only option to log out.

Since then, I tried to get rid of nvidia and get the system back on track using AMD GPU but it seems to be impossible so far!

First off, **prime-select has no option for amd** (but one for intel)[COLOR=#000000].
[/COLOR]
So I rebooted in recovery and uninstalled all nvidia drivers with:
```

dpkg -P $(dpkg -l | grep nvidia | awk '{print $2}')

```
I made sure nouveau and amdgpu were installed with:
```

apt install xserver-xorg-video-nouveau xserver-xorg-video-amdgpu

```
and rebooted.

Nothing has changed. The error message is still there.

The details are below:
```

# lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GA104M [GeForce RTX 3070 Mobile / Max-Q] (rev a1)
06:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [Radeon Vega Series / Radeon Vega Mobile Series] (rev c5)

# cat Xorg.0.log | grep \(EE\)
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

# cat Xorg.0.log | grep \(WW\)
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    63.675] (WW) Falling back to old probe method for modesetting
[    63.676] (WW) Falling back to old probe method for fbdev
[    63.763] (WW) AMDGPU(0): Option "HotplugDriver" is not used

# cat Xorg.0.log|grep -iP "(amd|nvidia|nouveau|Xorg)"
[    63.578] xorg-server 2:21.1.7-3ubuntu2.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    63.578] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 25 14:14:33 2024
[    63.579] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    63.579] (==) ModulePath set to "/usr/lib/xorg/modules"
[    63.593] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    63.594] (II) Applying OutputClass "AMDgpu" to /dev/dri/card1
[    63.594]     loading driver: amdgpu
[    63.661] (==) Matched amdgpu as autoconfigured driver 0
[    63.662] (II) LoadModule: "amdgpu"
[    63.662] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    63.662] (II) Module amdgpu: vendor="X.Org Foundation"
[    63.662] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    63.672] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    63.672] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    63.673] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    63.673] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[    63.676] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    63.676] (II) AMDGPU(0): Creating default Display subsection in Screen section
[    63.676] (==) AMDGPU(0): Depth 24, (--) framebuffer bpp 32
[    63.676] (II) AMDGPU(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    63.676] (==) AMDGPU(0): Default visual is TrueColor
[    63.676] (II) Applying OutputClass "AMDgpu" options to /dev/dri/card1
[    63.676] (==) AMDGPU(0): RGB weight 888
[    63.676] (II) AMDGPU(0): Using 8 bits per RGB (8 bit DAC)
[    63.676] (--) AMDGPU(0): Chipset: "AMD Radeon Graphics" (ChipID = 0x1638)
[    63.709] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    63.718] (II) AMDGPU(0): glamor X acceleration enabled on AMD Radeon Graphics (renoir, LLVM 15.0.7, DRM 3.54, 6.6.0-14-generic)
[    63.718] (II) AMDGPU(0): glamor detected, initialising EGL layer.
[    63.718] (==) AMDGPU(0): TearFree property default: auto
[    63.718] (==) AMDGPU(0): VariableRefresh: disabled
[    63.718] (==) AMDGPU(0): AsyncFlipSecondaries: disabled
[    63.718] (II) AMDGPU(0): KMS Pageflipping: enabled
[    63.721] (II) AMDGPU(0): Output eDP has no monitor section
[    63.730] (II) AMDGPU(0): EDID for output eDP
[    63.730] (II) AMDGPU(0): Manufacturer: AUO  Model: 978f  Serial#: 0
[    63.730] (II) AMDGPU(0): Year: 2020  Week: 3
[    63.730] (II) AMDGPU(0): EDID Version: 1.4
[    63.730] (II) AMDGPU(0): Digital Display Input
[    63.731] (II) AMDGPU(0): 8 bits per channel
[    63.731] (II) AMDGPU(0): Digital interface is DisplayPort
[    63.731] (II) AMDGPU(0): Max Image Size [cm]: horiz.: 38  vert.: 22
[    63.731] (II) AMDGPU(0): Gamma: 2.20
[    63.731] (II) AMDGPU(0): No DPMS capabilities specified
[    63.731] (II) AMDGPU(0): Supported color encodings: RGB 4:4:4 
[    63.731] (II) AMDGPU(0): First detailed timing is preferred mode
[    63.731] (II) AMDGPU(0): Preferred mode is native pixel format and refresh rate
[    63.731] (II) AMDGPU(0): Display is continuous-frequency
[    63.731] (II) AMDGPU(0): redX: 0.575 redY: 0.347   greenX: 0.352 greenY: 0.578
[    63.731] (II) AMDGPU(0): blueX: 0.161 blueY: 0.128   whiteX: 0.313 whiteY: 0.329
[    63.731] (II) AMDGPU(0): Manufacturer's mask: 0
[    63.731] (II) AMDGPU(0): Supported detailed timing:
[    63.731] (II) AMDGPU(0): clock: 368.1 MHz   Image Size:  382 x 215 mm
[    63.731] (II) AMDGPU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2102 h_border: 0
[    63.731] (II) AMDGPU(0): v_active: 1080  v_sync: 1090  v_sync_end 1095 v_blanking: 1216 v_border: 0
[    63.731] (II) AMDGPU(0): Supported detailed timing:
[    63.731] (II) AMDGPU(0): clock: 153.4 MHz   Image Size:  382 x 215 mm
[    63.731] (II) AMDGPU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2102 h_border: 0
[    63.731] (II) AMDGPU(0): v_active: 1080  v_sync: 1090  v_sync_end 1095 v_blanking: 1216 v_border: 0
[    63.731] (II) AMDGPU(0): Ranges: V min: 60 V max: 144 Hz, H min: 176 H max: 176 kHz, PixClock max 375 MHz
[    63.731] (II) AMDGPU(0):  B173HAN04.9
...
[    63.731] (II) Loading sub module "ramdac"
[    63.731] (II) LoadModule: "ramdac"
[    63.731] (II) Module "ramdac" already built-in
[    63.732] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    63.748] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    63.748] (II) AMDGPU(0): [DRI2] Setup complete
[    63.748] (II) AMDGPU(0): [DRI2]   DRI driver: radeonsi
[    63.748] (II) AMDGPU(0): [DRI2]   VDPAU driver: radeonsi
[    63.753] (II) AMDGPU(0): Front buffer pitch: 7680 bytes
[    63.753] (II) AMDGPU(0): SYNC extension fences enabled
[    63.753] (II) AMDGPU(0): Present extension enabled
[    63.753] (==) AMDGPU(0): DRI3 enabled
[    63.753] (==) AMDGPU(0): Backing store enabled
[    63.753] (II) AMDGPU(0): Direct rendering enabled
[    63.759] (II) AMDGPU(0): Use GLAMOR acceleration.
[    63.759] (II) AMDGPU(0): Acceleration enabled
[    63.759] (==) AMDGPU(0): DPMS enabled
[    63.759] (==) AMDGPU(0): Silken mouse enabled
[    63.759] (II) AMDGPU(0): Set up textured video (glamor)
[    63.763] (WW) AMDGPU(0): Option "HotplugDriver" is not used
[    63.771] (II) AMDGPU(0): Setting screen physical size to 508 x 285
[    63.815] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    64.061] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event12)
[    64.061] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[    64.062] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[    64.062] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[    64.280] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:03/i2c-0/i2c-ELAN050A:00/0018:04F3:31B1.0001/input/input27/event10"
[    64.283] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    64.408] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:03/i2c-0/i2c-ELAN050A:00/0018:04F3:31B1.0001/input/input29/event11"

# cat syslog|grep -iP "(amd|nvidia|nouveau|Xorg)"
Jan 25 14:13:48 hostname kernel: [    0.000000] Linux version 6.6.0-14-generic (buildd@lcy02-amd64-093) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-7ubuntu1) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.41) #14-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov 30 10:27:29 UTC 2023 (Ubuntu 6.6.0-14.14-generic 6.6.3)
Jan 25 14:13:48 hostname kernel: [    1.528110] nouveau: detected PR support, will not use DSM
Jan 25 14:13:48 hostname kernel: [    1.528534] nouveau 0000:01:00.0: enabling device (0000 -> 0003)
Jan 25 14:13:48 hostname kernel: [    1.529178] nouveau 0000:01:00.0: NVIDIA GA104 (b74000a1)
Jan 25 14:13:48 hostname kernel: [    1.668235] nouveau 0000:01:00.0: bios: version 94.04.43.00.9e
Jan 25 14:13:48 hostname kernel: [    1.670039] nouveau 0000:01:00.0: acr: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.670518] nouveau 0000:01:00.0: gr: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.670921] nouveau 0000:01:00.0: sec2: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.671492] nouveau 0000:01:00.0: fb: 8192 MiB GDDR6
Jan 25 14:13:48 hostname kernel: [    1.677559] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:13:48 hostname kernel: [    1.682540] nouveau 0000:01:00.0: DRM: VRAM: 8192 MiB
Jan 25 14:13:48 hostname kernel: [    1.682910] nouveau 0000:01:00.0: DRM: GART: 536870912 MiB
Jan 25 14:13:48 hostname kernel: [    1.683277] nouveau 0000:01:00.0: DRM: BIT table 'A' not found
Jan 25 14:13:48 hostname kernel: [    1.683633] nouveau 0000:01:00.0: DRM: BIT table 'L' not found
Jan 25 14:13:48 hostname kernel: [    1.683984] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
Jan 25 14:13:48 hostname kernel: [    1.684335] nouveau 0000:01:00.0: DRM: DCB version 4.1
Jan 25 14:13:48 hostname kernel: [    1.684682] nouveau 0000:01:00.0: DRM: DCB outp 00: 02012f52 00020010
Jan 25 14:13:48 hostname kernel: [    1.685045] nouveau 0000:01:00.0: DRM: DCB conn 02: 00010261
Jan 25 14:13:48 hostname kernel: [    1.685862] nouveau 0000:01:00.0: DRM: MM: using COPY for buffer copies
Jan 25 14:13:48 hostname kernel: [    1.687947] [drm] Initialized nouveau 1.4.0 20120801 for 0000:01:00.0 on minor 0
Jan 25 14:13:48 hostname kernel: [    1.689761] nouveau 0000:01:00.0: [drm] Cannot find any crtc or sizes
Jan 25 14:13:48 hostname kernel: [    1.691707] nouveau 0000:01:00.0: [drm] Cannot find any crtc or sizes
Jan 25 14:13:48 hostname kernel: [    1.693475] nouveau 0000:01:00.0: [drm] Cannot find any crtc or sizes
Jan 25 14:13:48 hostname kernel: [    3.118610] [drm] amdgpu kernel modesetting enabled.
Jan 25 14:13:48 hostname kernel: [    3.118982] amdgpu: vga_switcheroo: detected switching method \_SB_.PCI0.GP17.VGA_.ATPX handle
Jan 25 14:13:48 hostname kernel: [    3.119916] amdgpu: ATPX version 1, functions 
Jan 25 14:13:48 hostname kernel: [    3.120340] amdgpu: ATPX Hybrid Graphics
Jan 25 14:13:48 hostname kernel: [    3.124893] amdgpu: Virtual CRAT table created for CPU
Jan 25 14:13:48 hostname kernel: [    3.125261] amdgpu: Topology: Add CPU node
Jan 25 14:13:48 hostname kernel: [    3.125717] amdgpu 0000:06:00.0: enabling device (0006 -> 0007)
Jan 25 14:13:48 hostname kernel: [    3.132860] amdgpu 0000:06:00.0: amdgpu: Fetched VBIOS from VFCT
Jan 25 14:13:48 hostname kernel: [    3.133198] amdgpu: ATOM BIOS: 113-CEZANNE-018
Jan 25 14:13:48 hostname kernel: [    3.137724] amdgpu 0000:06:00.0: vgaarb: deactivate vga console
Jan 25 14:13:48 hostname kernel: [    3.137729] amdgpu 0000:06:00.0: amdgpu: Trusted Memory Zone (TMZ) feature enabled
Jan 25 14:13:48 hostname kernel: [    3.137735] amdgpu 0000:06:00.0: amdgpu: MODE2 reset
Jan 25 14:13:48 hostname kernel: [    3.138882] amdgpu 0000:06:00.0: amdgpu: VRAM: 512M
Jan 25 14:13:48 hostname kernel: [    3.138889] amdgpu 0000:06:00.0: amdgpu: GART: 1024M
Jan 25 14:13:48 hostname kernel: [    3.138894] amdgpu 0000:06:00.0: amdgpu: AGP: 267419648M
Jan 25 14:13:48 hostname kernel: [    3.139036] [drm] amdgpu: 512M of VRAM memory ready
Jan 25 14:13:48 hostname kernel: [    3.139041] [drm] amdgpu: 15721M of GTT memory ready.
Jan 25 14:13:48 hostname kernel: [    3.139854] amdgpu 0000:06:00.0: amdgpu: Will use PSP to load VCN firmware
Jan 25 14:13:48 hostname kernel: [    3.946794] amdgpu 0000:06:00.0: amdgpu: RAS: optional ras ta ucode is not available
Jan 25 14:13:48 hostname kernel: [    3.955338] amdgpu 0000:06:00.0: amdgpu: RAP: optional rap ta ucode is not available
Jan 25 14:13:48 hostname kernel: [    3.955348] amdgpu 0000:06:00.0: amdgpu: SECUREDISPLAY: securedisplay ta ucode is not available
Jan 25 14:13:48 hostname kernel: [    3.956370] amdgpu 0000:06:00.0: amdgpu: SMU is initialized successfully!
Jan 25 14:13:48 hostname kernel: [    4.139844] amdgpu: HMM registered 512MB device memory
Jan 25 14:13:48 hostname kernel: [    4.141090] kfd kfd: amdgpu: Allocated 3969056 bytes on gart
Jan 25 14:13:48 hostname kernel: [    4.141105] kfd kfd: amdgpu: Total number of KFD nodes to be created: 1
Jan 25 14:13:48 hostname kernel: [    4.141210] amdgpu: Virtual CRAT table created for GPU
Jan 25 14:13:48 hostname kernel: [    4.141688] amdgpu: Topology: Add dGPU node
Jan 25 14:13:48 hostname kernel: [    4.141693] kfd kfd: amdgpu: added device 1002:1638
Jan 25 14:13:48 hostname kernel: [    4.141764] amdgpu 0000:06:00.0: amdgpu: SE 1, SH per SE 1, CU per SH 8, active_cu_number 8
Jan 25 14:13:48 hostname kernel: [    4.141914] amdgpu 0000:06:00.0: amdgpu: ring gfx uses VM inv eng 0 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141919] amdgpu 0000:06:00.0: amdgpu: ring gfx_low uses VM inv eng 1 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141924] amdgpu 0000:06:00.0: amdgpu: ring gfx_high uses VM inv eng 4 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141929] amdgpu 0000:06:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 5 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141933] amdgpu 0000:06:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 6 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141938] amdgpu 0000:06:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 7 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141942] amdgpu 0000:06:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 8 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141947] amdgpu 0000:06:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 9 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141951] amdgpu 0000:06:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 10 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141956] amdgpu 0000:06:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 11 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141961] amdgpu 0000:06:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 12 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141965] amdgpu 0000:06:00.0: amdgpu: ring kiq_0.2.1.0 uses VM inv eng 13 on hub 0
Jan 25 14:13:48 hostname kernel: [    4.141970] amdgpu 0000:06:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 8
Jan 25 14:13:48 hostname kernel: [    4.141975] amdgpu 0000:06:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 8
Jan 25 14:13:48 hostname kernel: [    4.141979] amdgpu 0000:06:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 8
Jan 25 14:13:48 hostname kernel: [    4.141984] amdgpu 0000:06:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 8
Jan 25 14:13:48 hostname kernel: [    4.141988] amdgpu 0000:06:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 8
Jan 25 14:13:48 hostname kernel: [    4.143521] amdgpu 0000:06:00.0: amdgpu: [drm] Skipping amdgpu DM backlight registration
Jan 25 14:13:48 hostname kernel: [    4.143681] [drm] Initialized amdgpu 3.54.0 20150101 for 0000:06:00.0 on minor 1
Jan 25 14:13:48 hostname kernel: [    4.148806] fbcon: amdgpudrmfb (fb0) is primary device
Jan 25 14:13:48 hostname kernel: [    4.179117] amdgpu 0000:06:00.0: [drm] fb0: amdgpudrmfb frame buffer device
Jan 25 14:13:48 hostname kernel: [    6.185472] kvm_amd: TSC scaling supported
Jan 25 14:13:48 hostname kernel: [    6.186289] kvm_amd: Nested Virtualization enabled
Jan 25 14:13:48 hostname kernel: [    6.187018] kvm_amd: Nested Paging enabled
Jan 25 14:13:48 hostname kernel: [    6.187534] kvm_amd: Virtual VMLOAD VMSAVE supported
Jan 25 14:13:48 hostname kernel: [    6.187994] kvm_amd: Virtual GIF supported
Jan 25 14:13:48 hostname kernel: [    6.187994] kvm_amd: LBR virtualization supported
Jan 25 14:13:48 hostname kernel: [    6.251136] snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops nv50_audio_component_bind_ops [nouveau])
Jan 25 14:13:48 hostname sensors[1349]: amdgpu-pci-0600
Jan 25 14:13:48 hostname kernel: [   18.576715] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:13:59 hostname kernel: [   29.200590] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:13:59 hostname kernel: [   29.354345] Lockdown: Xorg: raw io port access is restricted; see man kernel_lockdown.7
Jan 25 14:13:59 hostname kernel: [   29.359858] nouveau 0000:01:00.0: vgaarb: VGA decodes changed: olddecodes=io+mem,decodes=none:owns=none
Jan 25 14:13:59 hostname kernel: [   29.359863] amdgpu 0000:06:00.0: vgaarb: VGA decodes changed: olddecodes=io+mem,decodes=none:owns=none
Jan 25 14:14:15 hostname kernel: [   45.095982] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:14:33 hostname kernel: [   63.500372] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:14:33 hostname kernel: [   63.673998] Lockdown: Xorg: raw io port access is restricted; see man kernel_lockdown.7

```
A few messages seem troubling:
```

Jan 25 14:13:48 hostname kernel: [    1.529178] nouveau 0000:01:00.0: NVIDIA GA104 (b74000a1)
Jan 25 14:13:48 hostname kernel: [    1.670039] nouveau 0000:01:00.0: acr: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.670518] nouveau 0000:01:00.0: gr: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.670921] nouveau 0000:01:00.0: sec2: firmware unavailable
Jan 25 14:13:48 hostname kernel: [    1.671492] nouveau 0000:01:00.0: fb: 8192 MiB GDDR6
Jan 25 14:13:48 hostname kernel: [    1.677559] nouveau 0000:01:00.0: fb: VPR locked, but no scrubber binary!
Jan 25 14:13:48 hostname kernel: [    1.683277] nouveau 0000:01:00.0: DRM: BIT table 'A' not found
Jan 25 14:13:48 hostname kernel: [    1.683633] nouveau 0000:01:00.0: DRM: BIT table 'L' not found
Jan 25 14:13:48 hostname kernel: [    1.689761] nouveau 0000:01:00.0: [drm] Cannot find any crtc or sizes

```
What am I missing?
Any suggestion?

---

### Post by grahammechanical on 2024-01-25
It is my understanding that using Advance options for Ubuntu>Linux kernel with recovery mode and then Resume should load to a desktop using the open source video driver. That was my experience when I was running a PC with a Nvidia graphics card. A reboot would load with the proprietary video driver. I would use Software and Updates>Additional Drivers tab to deactivate the proprietary video driver.

You may need to use a purge command to f=get rid of the Nvidia driver. Someone else on this forum may supply to correct command to do that.

Regards

---

### Post by actionmystique2 on 2024-01-26
At last, I tried to reconfigure Xorg as root in recovery with:
```

# Xorg -configure

```

which lead to:
```

[   192.131] 
X.Org X Server 1.21.1.7
X Protocol Version 11, Revision 0
[   192.132] Current Operating System: Linux hostname 6.6.0-14-generic #14-Ubuntu SMP PREEMPT_DYNAMIC Thu Nov 30 10:27:29 UTC 2023 x86_64
[   192.132] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.6.0-14-generic root=UUID=<uuid> ro single recovery nomodeset dis_ucode_ldr cgroup_enable=memory swapaccount=1
[   192.133] xorg-server 2:21.1.7-3ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[   192.133] Current version of pixman: 0.42.2
[   192.134]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   192.134] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   192.136] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 26 11:45:52 2024
[   192.136] (II) Loader magic: 0x64ac081c2020
[   192.136] (II) Module ABI versions:
[   192.136]     X.Org ANSI C Emulation: 0.4
[   192.136]     X.Org Video Driver: 25.2
[   192.136]     X.Org XInput driver : 24.4
[   192.136]     X.Org Server Extension : 10.0
[   192.136] (--) using VT number 2


[   192.136] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   192.141] (--) PCI: (1@0:0:0) 10de:249d:1025:151f rev 161, Mem @ 
[   192.141] (--) PCI:*(6@0:0:0) 1002:1638:1025:151f rev 197, Mem @ 
[   192.141] List of video drivers:
[   192.142]     amdgpu
[   192.142]     ati
[   192.142]     intel
[   192.143]     nouveau
[   192.143]     qxl
[   192.143]     radeon
[   192.144]     vmware
[   192.144]     modesetting
[   192.145]     fbdev
[   192.145]     vesa
[   192.145] (II) LoadModule: "amdgpu"
[   192.145] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[   192.147] (II) Module amdgpu: vendor="X.Org Foundation"
[   192.147]     compiled for 1.21.1.7, module version = 23.0.0
[   192.147]     Module class: X.Org Video Driver
[   192.147]     ABI class: X.Org Video Driver, version 25.2
[   192.147] (II) LoadModule: "ati"
[   192.147] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   192.147] (II) Module ati: vendor="X.Org Foundation"
[   192.147]     compiled for 1.21.1.3, module version = 19.1.0
[   192.147]     Module class: X.Org Video Driver
[   192.147]     ABI class: X.Org Video Driver, version 25.2
[   192.147] (II) LoadModule: "intel"
[   192.148] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   192.149] (II) Module intel: vendor="X.Org Foundation"
[   192.149]     compiled for 1.21.1.3, module version = 2.99.917
[   192.149]     Module class: X.Org Video Driver
[   192.149]     ABI class: X.Org Video Driver, version 25.2
[   192.149] (II) LoadModule: "nouveau"
[   192.149] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   192.150] (II) Module nouveau: vendor="X.Org Foundation"
[   192.150]     compiled for 1.21.1.3, module version = 1.0.17
[   192.150]     Module class: X.Org Video Driver
[   192.150]     ABI class: X.Org Video Driver, version 25.2
[   192.150] (II) LoadModule: "qxl"
[   192.150] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[   192.151] (II) Module qxl: vendor="X.Org Foundation"
[   192.151]     compiled for 1.21.1.7, module version = 0.1.6
[   192.151]     Module class: X.Org Video Driver
[   192.151]     ABI class: X.Org Video Driver, version 25.2
[   192.151] (II) LoadModule: "radeon"
[   192.151] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   192.152] (II) Module radeon: vendor="X.Org Foundation"
[   192.152]     compiled for 1.21.1.3, module version = 19.1.0
[   192.152]     Module class: X.Org Video Driver
[   192.152]     ABI class: X.Org Video Driver, version 25.2
[   192.152] (II) LoadModule: "vmware"
[   192.152] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[   192.246] (II) Module vmware: vendor="X.Org Foundation"
[   192.246]     compiled for 1.21.1.4, module version = 13.3.0
[   192.246]     Module class: X.Org Video Driver
[   192.246]     ABI class: X.Org Video Driver, version 25.2
[   192.246] (II) LoadModule: "modesetting"
[   192.246] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   192.246] (II) Module modesetting: vendor="X.Org Foundation"
[   192.246]     compiled for 1.21.1.7, module version = 1.21.1
[   192.246]     Module class: X.Org Video Driver
[   192.246]     ABI class: X.Org Video Driver, version 25.2
[   192.246] (II) LoadModule: "fbdev"
[   192.246] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   192.247] (II) Module fbdev: vendor="X.Org Foundation"
[   192.247]     compiled for 1.21.1.3, module version = 0.5.0
[   192.247]     Module class: X.Org Video Driver
[   192.247]     ABI class: X.Org Video Driver, version 25.2
[   192.247] (II) LoadModule: "vesa"
[   192.247] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   192.247] (II) Module vesa: vendor="X.Org Foundation"
[   192.247]     compiled for 1.21.1.3, module version = 2.5.0
[   192.247]     Module class: X.Org Video Driver
[   192.247]     ABI class: X.Org Video Driver, version 25.2
[   192.248] xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)
[   192.248] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[   192.248] (II) NOUVEAU driver Date:   Sat Jan 23 12:24:42 2021 -0500
[   192.248] (II) NOUVEAU driver for NVIDIA chipset families :
[   192.248]     RIVA TNT            (NV04)
[   192.248]     RIVA TNT2           (NV05)
[   192.248]     GeForce 256         (NV10)
[   192.248]     GeForce 2           (NV11, NV15)
[   192.248]     GeForce 4MX         (NV17, NV18)
[   192.248]     GeForce 3           (NV20)
[   192.248]     GeForce 4Ti         (NV25, NV28)
[   192.248]     GeForce FX          (NV3x)
[   192.248]     GeForce 6           (NV4x)
[   192.248]     GeForce 7           (G7x)
[   192.248]     GeForce 8           (G8x)
[   192.248]     GeForce 9           (G9x)
[   192.248]     GeForce GTX 2xx/3xx (GT2xx)
[   192.248]     GeForce GTX 4xx/5xx (GFxxx)
[   192.248]     GeForce GTX 6xx/7xx (GKxxx)
[   192.248]     GeForce GTX 9xx     (GMxxx)
[   192.248]     GeForce GTX 10xx    (GPxxx)
[   192.248] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   192.248] (II) FBDEV: driver for framebuffer: fbdev
[   192.248] (II) VESA: driver for VESA chipsets: vesa
[   192.440] (++) Using config file: "/root/xorg.conf.new"
[   192.441] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   192.442] (==) ServerLayout "layout"
[   192.442] (**) |-->Screen "Screen0" (0)
[   192.442] (**) |   |-->Monitor "Monitor0"
[   192.443] (**) |   |-->Device "Card0"
[   192.443] (**) |   |-->GPUDevice "Card1"
[   192.443] (==) Automatically adding devices
[   192.443] (==) Automatically enabling devices
[   192.443] (==) Automatically adding GPU devices
[   192.443] (==) Automatically binding GPU devices
[   192.443] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   192.443] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   192.443]     Entry deleted from font path.
[   192.443] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   192.443] (**) ModulePath set to "/usr/lib/xorg/modules"
[   192.443] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   192.443] (II) AMDGPU(0): [KMS] Kernel modesetting enabled.
[   192.444] (EE) AMDGPU(0): [drm] Failed to open DRM device for pci:0000:06:00.0: No such file or directory
[   192.570] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -19
[   192.571] Number of created screens does not match number of detected devices.
  Configuration failed.
[   192.571] (EE) Server terminated with error (2). Closing log file.

```
The message **xf86EnableIO: failed to enable I/O ports 0000-03ff (Operation not permitted)** is very troubling.

---

### Post by MAFoElffen on 2024-01-27
Where and who told you to install package 'linux-modules-nvidia-535-generic'?

If installing NVidia drivers from the repo's, all you have to do is either
```

sudo apt install --yes nvidia-driver-535
# OR
sudo apt install --yes nvidia-driver-535 nvidia-dkms-535

```
Doing either of those will pull in what else it needs as dependencies automatically.

What i recommend to people to reinstall NVidia drivers, is to first purge the old drivers using
```

sudo apt remove --purge --yes nvidia* libnvidia*

```
That gets rid of all fragments of the drivers and their dependencies.

Are you taken care of now? It seems so from what I can see. Any other questions?

---

### Post by actionmystique2 on 2024-01-29
1. Despite what you think:
```

sudo apt remove --yes nvidia* libnvidia*

```
does NOT "[COLOR=#000000]get rid of all fragments of the drivers and their dependencies" as it leaves behind all configuration.

[/COLOR]2. "[COLOR=#000000]getting rid of all fragments of the drivers and their dependencies" has already been done as described in my first post:
[/COLOR]```

# dpkg -P $(dpkg -l | grep nvidia | awk '{print $2}')

```
is even more powerful than
```

# apt purge --yes nvidia* libnvidia*

```
as the former purges all packages involved with nvidia (such as [COLOR=#000000]linux-modules-nvidia-535-generic for instance) which the latter does not.

So obviously, the issue remains.[/COLOR]

---

### Post by MAFoElffen on 2024-01-29
Editted previous commend. Must have been in a hurry. Meant for if from repos.

---

