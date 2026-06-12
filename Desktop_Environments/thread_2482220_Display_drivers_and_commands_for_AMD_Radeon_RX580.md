---
title: "Display drivers and commands for AMD Radeon RX580"
date: 2022-12-24
forum: Desktop Environments
---

### Post by jiapei100 on 2022-12-24
I'm testing and AMD GPU Radeon RX 580 .

```

&#10140;  ~ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: Radeon RX 580 Series (polaris10, LLVM 15.0.3, DRM 3.49, 5.15.0-56-generic) (0x67df)
    Version: 22.3.0
    Accelerated: yes
    Video memory: 8192MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.6
    Max compat profile version: 4.6
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 7710 MB, largest block: 7710 MB
    VBO free aux. memory - total: 7922 MB, largest block: 7922 MB
    Texture free memory - total: 7710 MB, largest block: 7710 MB
    Texture free aux. memory - total: 7922 MB, largest block: 7922 MB
    Renderbuffer free memory - total: 7710 MB, largest block: 7710 MB
    Renderbuffer free aux. memory - total: 7922 MB, largest block: 7922 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 8192 MB
    Total available memory: 16171 MB
    Currently available dedicated video memory: 7710 MB
OpenGL vendor string: AMD
OpenGL renderer string: Radeon RX 580 Series (polaris10, LLVM 15.0.3, DRM 3.49, 5.15.0-56-generic)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 22.3.0-devel
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.6 (Compatibility Profile) Mesa 22.3.0-devel
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.3.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

```


[LIST=1]
[*] I've been thinking this GPU should have **NOTHING** to do with Nvidia. However, **inxi** gives me the following info:

```
&#10140;  ~ inxi -G                
Graphics:
  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
    driver: amdgpu v: 5.18.13
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell v: 42.5 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: amdgpu
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Radeon RX 580 Series (polaris10 LLVM 15.0.3 DRM 3.49
  5.15.0-56-generic)
    v: 4.6 Mesa 22.3.0-devel

```

Is it saying that my **wayland server** still has **nvidia** loaded? However, I don't even have **nvidia-driver** installed.... 
```
&#10140;  ~ nvidia-smi          
zsh: command not found: nvidia-smi

```


[*] I **ALSO** think the current resolution should be as displayed as **Full HD (1080P)**, but **lshw** shows only **1360x768** is configured .
```

&#10140;  ~ sudo lshw -C display
[sudo] password for XXXXXXXX: 
  *-display                 
       description: VGA compatible controller
       product: Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=amdgpu latency=0 resolution=1360,768
       resources: irq:38 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:f7e00000-f7e3ffff memory:c0000-dffff

```

[/LIST]

So, can anybody help to explain why it is so? And how can I get the correct/expected answer from those commands?

---

### Post by Tadaen_Sylvermane on 2022-12-25
I know for Xorg the main drivers are installed. Just used when necessary. They aren't doing anything and are all dependencies of Xorg. Assuming Wayland is the same they are just there. Same way Windows has a good number of default drivers built in. That way if it did detect an Nvidia card it would load and be able to use it.

Also if you look at it you will see that nouveau is unloaded. Not being used.

---

### Post by jiapei100 on 2022-12-31
Thank you @Tadaen_Sylvermane.

I noticed it looks like a kernel issue: please refer to : [https://www.mail-archive.com/search?l=ubuntu-bugs@lists.ubuntu.com&q=subject:%22%5C%5BBug+1834771%5C%5D+Re%5C%3A+No+HDMI%5C-audio+after+kernel+4.15.%5C-0.50%22&o=newest&f=1]("https://www.mail-archive.com/search?l=ubuntu-bugs@lists.ubuntu.com&q=subject:%22%5C%5BBug+1834771%5C%5D+Re%5C%3A+No+HDMI%5C-audio+after+kernel+4.15.%5C-0.50%22&o=newest&f=1")

What's more:

```

&#10140;  lspci -nnk | grep -iA2 vga 
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] [1002:67df] (rev e7)
	Subsystem: XFX Pine Group Inc. Radeon RX 580 [1682:c580]
	Kernel driver in use: amdgpu
&#10140;  lsmod | grep nvidia        
&#10140;  lsmod | grep nouveau
&#10140;  lsmod | grep amdgpu 
amdgpu              12800000  27
amddrm_ttm_helper      16384  1 amdgpu
amdttm                 94208  2 amdgpu,amddrm_ttm_helper
iommu_v2               24576  1 amdgpu
amd_sched              45056  1 amdgpu
amdkcl                 28672  3 amd_sched,amdttm,amdgpu
drm_kms_helper        311296  3 amdgpu
drm                   622592  13 drm_kms_helper,amd_sched,amdttm,amdgpu,amddrm_ttm_helper
i2c_algo_bit           16384  1 amdgpu
&#10140;  inxi -Gx
Graphics:
  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590]
    vendor: XFX Pine driver: amdgpu v: 5.18.13 bus-ID: 01:00.0
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: amdgpu
    gpu: amdgpu resolution: 1920x1080~60Hz
  OpenGL: renderer: Radeon RX 580 Series (polaris10 LLVM 15.0.3 DRM 3.49
  5.15.0-56-generic)
    v: 4.6 Mesa 22.3.0-devel direct render: Yes
&#10140;  sudo lshw -class video | grep driver=
[sudo] password for XXXXXXXXXX: 
       configuration: depth=32 driver=amdgpu latency=0 resolution=1360,768

```

Particularly, why the **LAST** two command give out 2 different resolution?
- 1920x1080
- 1360x768


Anyway, this above commands clearly show that **AMD RX580** is working fine with video display via HDMI, but **NO audio** via HDMI.

---

