---
title: "ACPI BIOS Error (bug)"
date: 2022-07-27
forum: Desktop Environments
---

### Post by oygle on 2022-07-27
Have installed a fresh 22.04 in the last few days. This comes up everytime on boot

> 
Jul 28 07:40:03 Inspiron-3542 kernel: [    2.479236] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:08:00.0 on minor 0
Jul 28 07:40:03 Inspiron-3542 kernel: [    2.479623] [drm] Initialized i915 1.6.0 20201103 for 0000:00:02.0 on minor 1
Jul 28 07:40:03 Inspiron-3542 kernel: [    2.480737] ACPI: video: [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
Jul 28 07:40:03 Inspiron-3542 kernel: [    2.481683] ACPI: video: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
Jul 28 07:40:03 Inspiron-3542 kernel: [    2.481695] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GFX0.DD02._BCL], AE_NOT_FOUND (20210730/psargs-330)


```
$ ubuntu-drivers devices
```

> == /sys/devices/pci0000:00/0000:00:1c.4/0000:08:00.0 ==
modalias : pci:v000010DEd00001341sv00001028sd00000653bc03sc02i00
vendor   : NVIDIA Corporation
model    : GM108M [GeForce 840M]
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-510-server - distro non-free
driver   : nvidia-driver-515 - distro non-free recommended
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-515-server - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-510 - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

so this was installed ..

```
sudo apt-get install nvidia-driver-515
```

```
sudo lshw -C display
```

> *-display                 
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1366,768
       resources: irq:48 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:47 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff
       
```
dpkg -l | grep -i Nvidia
```

> ii  libnvidia-cfg1-515:amd64                      515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-515                          515.48.07-0ubuntu0.22.04.2                  all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-515:amd64                   515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-515:i386                    515.48.07-0ubuntu0.22.04.2                  i386         NVIDIA libcompute package
ii  libnvidia-decode-515:amd64                    515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-515:i386                     515.48.07-0ubuntu0.22.04.2                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64                  1:1.1.9-1.1                                 amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-515:amd64                    515.48.07-0ubuntu0.22.04.2                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-515:i386                     515.48.07-0ubuntu0.22.04.2                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-515:amd64                     515.48.07-0ubuntu0.22.04.2                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-515:amd64                      515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-515:i386                       515.48.07-0ubuntu0.22.04.2                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-515:amd64                        515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-515:i386                         515.48.07-0ubuntu0.22.04.2                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  nvidia-compute-utils-515                      515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA compute utilities
ii  nvidia-dkms-515                               515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA DKMS package
ii  nvidia-driver-515                             515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-515                      515.48.07-0ubuntu0.22.04.2                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-515                      515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA kernel source package
ii  nvidia-prime                                  0.8.17.1                                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                               510.47.03-0ubuntu1                          amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-515                              515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                       0.18.2                                      all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-515                 515.48.07-0ubuntu0.22.04.2                  amd64        NVIDIA binary Xorg driver

The Dell Inspiron manual states "Dell manual  -  490-BBVU : NVIDIA(R) GeForce(R) 840M 2GB DDR3L"

---

### Post by pantazi on 2022-07-28
Similar to this recent update on Ubuntu 20.04.

[https://ubuntuforums.org/showthread.php?t=2477426](https://ubuntuforums.org/showthread.php?t=2477426)

---

### Post by oygle on 2022-07-28
> **pantazi said:**
> Similar to this recent update on Ubuntu 20.04.

[https://ubuntuforums.org/showthread.php?t=2477426](https://ubuntuforums.org/showthread.php?t=2477426)

Okay thanks, I'll check it out.

---

