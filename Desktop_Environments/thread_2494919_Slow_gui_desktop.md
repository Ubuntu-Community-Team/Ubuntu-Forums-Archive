---
title: "Slow gui desktop"
date: 2024-01-31
forum: Desktop Environments
---

### Post by honzap00 on 2024-01-31
Hello,
I have an HP Probook G9 laptop with an i5 12th gen, 16GB RAM, Ubuntu LTS  22.04, and the system occasionally feels slow - GUI
The installation is  fresh. 
Could you please recommend what to focus on? A memtest pass ok.  

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:46a8] (rev 0c)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company Device [103c:8a9e]
    Kernel driver in use: i915
model name    : 12th Gen Intel(R) Core(TM) i5-1235U

```

Thanks

---

### Post by TheFu on 2024-01-31
Can't tell from what's been provided.

Check the system logs for warnings and errors. Google "ubuntu log files" if you don't know how to view and search them.

For providing system hardware overview, run  **inxi -Fxz**
That tool may need to be installed.  **sudo apt update; sudo apt install inxi** will do that.  It is a good tool for overview of system. It will answer hardware, driver, environment questions with 1 command.  When posting the output, wrap it in forum code tags, so things line up.  Use the "Advanced" editor with the "#" button to do that.

Is the system slow or just the GUI?  Is the GUI slow always or just sometimes?  What else is running when it is slow?

---

### Post by ActionParsnip on 2024-01-31
What is the output of
```

sudo dmidecode -t 1

```
Also, which desktop environment are you using? Do you dual boot with Windows?

---

### Post by honzap00 on 2024-02-01
> **ActionParsnip said:**
> What is the output of
```

sudo dmidecode -t 1

```
Also, which desktop environment are you using? Do you dual boot with Windows?


Ubuntu Gnome, No only ubuntu 

```
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.4 present.

Handle 0x0013, DMI type 1, 27 bytes
System Information
    Manufacturer: HP
    Product Name: HP ProBook 440 14 inch G9 Notebook PC
    UUID: a7ce177a-fb68-40f5-b51a-70219418eb2f
    Wake-up Type: Power Switch
    SKU Number: 6S6J2EA#BCM
    Family: 103C_5336AN HP ProBook

```

---

### Post by honzap00 on 2024-02-01
```
inxi -Fxz
System:
  Kernel: 6.5.0-15-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)

Machine:
  Type: Laptop System: HP product: HP ProBook 440 14 inch G9 Notebook PC
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A9E v: KBC Version 21.09.00 serial: <superuser required>
    UEFI: HP v: U85 Ver. 01.04.00 date: 08/24/2022

Battery:
  ID-1: BAT0 charge: 34.5 Wh (100.0%) condition: 34.5/42.8 Wh (80.7%)
    volts: 12.4 min: 11.4 model: Hewlett-Packard Primary status: Full
  Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard
    charge: 55% (should be ignored) status: Discharging

CPU:
  Info: 10-core (2-mt/8-st) model: 12th Gen Intel Core i5-1235U bits: 64
    type: MST AMCP arch: Alder Lake rev: 4 cache: L1: 928 KiB L2: 6.5 MiB
    L3: 12 MiB
  Speed (MHz): avg: 1341 high: 2500 min/max: N/A cores: 1: 778 2: 843
    3: 678 4: 517 5: 829 6: 2500 7: 2500 8: 747 9: 2500 10: 803 11: 2500
    12: 900 bogomips: 59904
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx

Graphics:
  Device-1: Intel vendor: Hewlett-Packard driver: i915 v: kernel
    bus-ID: 00:02.0
  Device-2: Chicony HP HD Camera type: USB driver: uvcvideo bus-ID: 3-1:2
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 resolution: 3840x2160~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes

Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Device-2: GN Netcom enc060:Buttons Volume up/down/mute + phone [Jabra]
    type: USB driver: jabra,snd-usb-audio,usbhid bus-ID: 3-2.1:5
  Sound Server-1: ALSA v: k6.5.0-15-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlp0s20f3 state: down mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: fctvpn74adcdb5 state: up speed: 10000 Mbps duplex: full mac: N/A

Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus-ID: 3-10:6
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>

Drives:
  Local Storage: total: 476.94 GiB used: 32.59 GiB (6.8%)
  ID-1: /dev/nvme0n1 vendor: SK Hynix model: BC711 HFM512GD3JX013N
    size: 476.94 GiB temp: 33.9 C

Partition:
  ID-1: / size: 464.35 GiB used: 32.27 GiB (7.0%) fs: ext4 dev: /dev/dm-1
    mapped: vgubuntu-root
  ID-2: /boot size: 1.61 GiB used: 309.1 MiB (18.8%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-3: /boot/efi size: 511 MiB used: 14.3 MiB (2.8%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 1.91 GiB used: 0 KiB (0.0%)
    dev: /dev/dm-2 mapped: vgubuntu-swap_1

Sensors:
  System Temperatures: cpu: 54.0 C mobo: 25.0 C
  Fan Speeds (RPM): N/A

Info:
  Processes: 369 Uptime: 2h 22m Memory: 15.29 GiB used: 6.86 GiB (44.9%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 1917 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

---

### Post by honzap00 on 2024-02-01
> **TheFu said:**
> 

Is the system slow or just the GUI?  Is the GUI slow always or just sometimes?  What else is running when it is slow?

The system was at its slowest when "isolated plus" was visible in the processes because of firefox - I adjusted this in 
```
https://askubuntu.com/questions/1466241/firefox-isolate-process-cpu-usage-100
```

Even so, there is a slow display as if the system is stressed

---

### Post by TheFu on 2024-02-01
That laptop should be able to handle anything normal.  It will struggle with video editing and gaming, but anything else should be fine that doesn't require a better GPU.
For my taste, the swap file size is a little small, but you aren't using any of it, so that isn't the current issue.

I see you are setup with LVM. Typically, that happens only when LUKS encryption is selected at install or someone specifically requests LVM to be used.  I always do for flexibility, but most people don't.

The only software item that seems odd to me is the v6.x kernel.  My 22.04-based Desktop still uses the 5.15.x kernel. There have been a few performance "regressions" against the 6.x kernels, but I haven't kept up with those.  You might look for performance issues with your specific kernel.  To see if that's it, try booting from the last kernel that worked fine. Usually 3 kernels are retained in the Advanced Grub Menu.  It would be good to know if all kernels or just 1 are slow.  I did see a few reports that running virtual machines under a v6.5.x kernel had huge performance issues.

I'm not a fan of Wayland, though it should be faster than Xorg (X11), you might try choosing that mode on the login screen to see if it helps. I doubt it will, but something to try and isolate the problem.

Next time the system gets slow, look at what is running using top, htop, or glances.  I have some suspicions, but don't want to taint the actual results.

Did you check the system logs for problems yet?

---

### Post by TheFu on 2024-02-01
> **honzap00 said:**
> The system was at its slowest when "isolated plus" was visible in the processes because of firefox - I adjusted this in 
```
https://askubuntu.com/questions/1466241/firefox-isolate-process-cpu-usage-100
```

Even so, there is a slow display as if the system is stressed

The default version of firefox is a snap package.  Install a non-Snap version instead, then remove the snap version of firefox.
I've been using Firefox ESR for this reason.  Snaps break lots of my workflows.  So does Wayland, so I avoid both on desktops.

---

### Post by MAFoElffen on 2024-02-01
Do you have Mesa and Vulkan drivers installed? Which versions?
```

mafoelffen@msi-ubuntu:~$ vulkaninfo --summary | sed -n '/Devices:/,$p'
'DISPLAY' environment variable not set... skipping surface info
Devices:
========
GPU0:
    apiVersion         = 4206834 (1.3.242)
    driverVersion      = 2246476096 (0x85e68140)
    vendorID           = 0x10de
    deviceID           = 0x2182
    deviceType         = PHYSICAL_DEVICE_TYPE_DISCRETE_GPU
    deviceName         = NVIDIA GeForce GTX 1660 Ti
    driverID           = DRIVER_ID_NVIDIA_PROPRIETARY
    driverName         = NVIDIA
    driverInfo         = 535.154.05
    conformanceVersion = 1.3.5.0
    deviceUUID         = 568d56d8-5ee0-8e84-ae3d-4aa996e4fd51
    driverUUID         = 02b61036-1a0b-5721-99e2-071d493de8ce
GPU1:
    apiVersion         = 4206859 (1.3.267)
    driverVersion      = 1 (0x0001)
    vendorID           = 0x10005
    deviceID           = 0x0000
    deviceType         = PHYSICAL_DEVICE_TYPE_CPU
    deviceName         = llvmpipe (LLVM 15.0.7, 256 bits)
    driverID           = DRIVER_ID_MESA_LLVMPIPE
    driverName         = llvmpipe
    driverInfo         = Mesa 24.0.0-devel (git-3ca1f35cbf) (LLVM 15.0.7)
    conformanceVersion = 1.3.1.1
    deviceUUID         = 6d657361-3234-2e30-2e30-2d6465766500
    driverUUID         = 6c6c766d-7069-7065-5555-494400000000
GPU2:
    apiVersion         = 4206859 (1.3.267)
    driverVersion      = 96874595 (0x5c63063)
    vendorID           = 0x8086
    deviceID           = 0xa780
    deviceType         = PHYSICAL_DEVICE_TYPE_INTEGRATED_GPU
    deviceName         = Intel(R) Graphics (RPL-S)
    driverID           = DRIVER_ID_INTEL_OPEN_SOURCE_MESA
    driverName         = Intel open-source Mesa driver
    driverInfo         = Mesa 24.0.0-devel (git-3ca1f35cbf)
    conformanceVersion = 1.3.6.0
    deviceUUID         = 868080a7-0400-0000-0002-000000000000
    driverUUID         = aff3446c-d7df-06c8-4793-4fd1ccc03d7d
mafoelffen@msi-ubuntu:~$ clinfo | grep -E 'Platform Name|Platform Vendor|Platform Version|ICD loader'
  Platform Name                                   NVIDIA CUDA
  Platform Vendor                                 NVIDIA Corporation
  Platform Version                                OpenCL 3.0 CUDA 12.2.148
  Platform Name                                   Intel(R) OpenCL Graphics
  Platform Vendor                                 Intel(R) Corporation
  Platform Version                                OpenCL 3.0 
  Platform Name                                   NVIDIA CUDA
  Platform Name                                   Intel(R) OpenCL Graphics
ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.14
  ICD loader Profile                              OpenCL 3.0
mafoelffen@msi-ubuntu:~$ sudo xpu-smi discovery -d 0 | head -n18
+-----------+--------------------------------------------------------------------------------------+
| Device ID | Device Information                                                                   |
+-----------+--------------------------------------------------------------------------------------+
| 0         | Device Type: GPU                                                                     |
|           | Device Name: Intel(R) UHD Graphics 770                                               |
|           | PCI Device ID: 0xa780                                                                |
|           | Vendor Name: Intel(R) Corporation                                                    |
|           | SOC UUID: 00000000-0000-0200-0000-0004a7808086                                       |
|           | Serial Number: unknown                                                               |
|           | Core Clock Rate: 1650 MHz                                                            |
|           | Stepping: B0                                                                         |
|           | SKU Type: N/A                                                                        |
|           |                                                                                      |
|           | Driver Version: N/A                                                                  |
|           | Kernel Version: 6.5.0-14-generic                                                     |
|           | GFX Firmware Name: GFX                                                               |
|           | GFX Firmware Version: unknown                                                        |
|           | GFX Firmware Status: unknown                                                         |
mafoelffen@msi-ubuntu:~$ vainfo | head -n5
error: can't connect to X server!
libva info: VA-API version 1.20.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_20
libva info: va_openDriver() returns 0
Trying display: wayland
Trying display: x11
Trying display: drm
vainfo: VA-API version: 1.20 (libva 2.20.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 23.4.0 ()
mafoelffen@msi-ubuntu:~$ apt list intel-* --installed
Listing... Done
intel-gpu-tools/jammy,now 1.26-2 amd64 [installed]
intel-gsc/unknown,now 0.8.9+65~u22.04 amd64 [installed,automatic]
intel-igc-cm/unknown,now 1.0.206-775~22.04 amd64 [installed,automatic]
intel-level-zero-gpu/unknown,now 1.3.27191.42-775~22.04 amd64 [installed]
intel-media-va-driver-non-free/unknown,now 23.4.0-775~22.04 amd64 [installed]
intel-metrics-discovery/unknown,now 1.12.169-775~22.04 amd64 [installed,automatic]
intel-metrics-library/unknown,now 1.0.152-760~22.04 amd64 [installed,automatic]
intel-microcode/jammy-updates,jammy-security,now 3.20231114.0ubuntu0.22.04.1 amd64 [installed,automatic]
intel-opencl-icd/unknown,now 23.35.27191.42-775~22.04 amd64 [installed]
mafoelffen@msi-ubuntu:~$ apt list intel-media-va-driver-non-free --installed
Listing... Done
intel-media-va-driver-non-free/unknown,now 23.4.0-775~22.04 amd64 [installed]
N: There are 6 additional versions. Please use the '-a' switch to see them.
mafoelffen@msi-ubuntu:~$ clinfo | grep -E 'Platform Name|Platform Vendor|Platform Version|ICD loader'
  Platform Name                                   NVIDIA CUDA
  Platform Vendor                                 NVIDIA Corporation
  Platform Version                                OpenCL 3.0 CUDA 12.2.148
  Platform Name                                   Intel(R) OpenCL Graphics
  Platform Vendor                                 Intel(R) Corporation
  Platform Version                                OpenCL 3.0 
  Platform Name                                   NVIDIA CUDA
  Platform Name                                   Intel(R) OpenCL Graphics
ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.14
  ICD loader Profile                              OpenCL 3.0
mafoelffen@msi-ubuntu:~$ sudo xpu-smi discovery -d 0 | head -n18
+-----------+--------------------------------------------------------------------------------------+
| Device ID | Device Information                                                                   |
+-----------+--------------------------------------------------------------------------------------+
| 0         | Device Type: GPU                                                                     |
|           | Device Name: Intel(R) UHD Graphics 770                                               |
|           | PCI Device ID: 0xa780                                                                |
|           | Vendor Name: Intel(R) Corporation                                                    |
|           | SOC UUID: 00000000-0000-0200-0000-0004a7808086                                       |
|           | Serial Number: unknown                                                               |
|           | Core Clock Rate: 1650 MHz                                                            |
|           | Stepping: B0                                                                         |
|           | SKU Type: N/A                                                                        |
|           |                                                                                      |
|           | Driver Version: N/A                                                                  |
|           | Kernel Version: 6.5.0-14-generic                                                     |
|           | GFX Firmware Name: GFX                                                               |
|           | GFX Firmware Version: unknown                                                        |
|           | GFX Firmware Status: unknown                                                         |
mafoelffen@msi-ubuntu:~$ vainfo | head -n5
error: can't connect to X server!
libva info: VA-API version 1.20.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_20
libva info: va_openDriver() returns 0
Trying display: wayland
Trying display: x11
Trying display: drm
vainfo: VA-API version: 1.20 (libva 2.20.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 23.4.0 ()
mafoelffen@msi-ubuntu:~$ apt list intel-media-va-driver-non-free --installed
Listing... Done
intel-media-va-driver-non-free/unknown,now 23.4.0-775~22.04 amd64 [installed]
N: There are 6 additional versions. Please use the '-a' switch to see them.

```

---

### Post by TheFu on 2024-02-01
> **MAFoElffen said:**
> Do you have Mesa and Vulkan drivers installed? Which versions?

I don't have Vulkan anything.

```
$ vulkaninfo --summary | sed -n '/Devices:/,$p'

Command 'vulkaninfo' not found, but can be installed with:

sudo apt install vulkan-tools
```

I can transcode video to h.265 with good-to-great results using the iGPU on my Ryzen, however, so I definitely have mesa supported. I'm using the va-api interface.  Just tweaked the transcode script to get the right target bitrate for my quality+filesize needs.  Seems 3Mbps is optimal for 1080p stuff to have the filesize smaller than handbrake creates in about 6x the time.  5Mbps creates a file that is larger, but only slightly better quality that is hard to notice.  Of course, the handbrake transcode quality is better.  I haven't figured out the way to get better quality in the hardware transcode besides upping the video bitrate.  So, for long term archival, I'll stick with handbrake transcodes, but there's a bunch of watch-once content for which a fast, good-enough, transcoding is acceptable.

BTW, I understand the iGPU on Intel is more mature at this. I don't have any Intel CPUs in daily use anymore.

---

### Post by MAFoElffen on 2024-02-02
Mesa ad Vulkan help with Intel Graphics greatly. Just because 'vulkan-tools' is not installed does not mean that vulkan is installed or not. That was an optional.

What they also do not tell you, is that Intel Iris XE GPU's reserve about 4GB of the RAM for it's own use. So if thinking that 16GB is allot, and have thing loaded, take off that 4GB of memory for the graphics while you are crunching the numbers.


I would usually recommend for 11th Gen and newer going to the Intel XE OOT Extended Graphics drivers, except... They do not work yet with the 6.5.0 kernels. I am still working with the two upstream Intel Graphics Support Teams on the getting those drivers to work with those. The normal in-kernel i915 driver does still work.

---

### Post by honzap00 on 2024-02-05
> **TheFu said:**
> 
I see you are setup with LVM. Typically, that happens only when LUKS encryption is selected at install or someone specifically requests LVM to be used.  I always do for flexibility, but most people don't.

The only software item that seems odd to me is the v6.x kernel.  My 22.04-based Desktop still uses the 5.15.x kernel. There have been a few performance "regressions" against the 6.x kernels, but I haven't kept up with those.  You might look for performance issues with your specific kernel.  To see if that's it, try booting from the last kernel that worked fine. Usually 3 kernels are retained in the Advanced Grub Menu.  It would be good to know if all kernels or just 1 are slow.  I did see a few reports that running virtual machines under a v6.5.x kernel had huge performance issues.

I'm not a fan of Wayland, though it should be faster than Xorg (X11), you might try choosing that mode on the login screen to see if it helps. I doubt it will, but something to try and isolate the problem.

Next time the system gets slow, look at what is running using top, htop, or glances.  I have some suspicions, but don't want to taint the actual results.

Did you check the system logs for problems yet?


I have LVM because it was an option for encryption, and encryption is mandatory at work.

In the advanced kernel, I only have versions 6.X; there are no others.


During login, I selected Xorg - we'll see. 
I went through the logs, but I didn't find anything... but I have to say, I'm not an expert, and I might have overlooked something fatal.

---

### Post by honzap00 on 2024-02-06
> **TheFu said:**
>   My 22.04-based Desktop still uses the 5.15.x kernel. There have been a few performance "regressions" against the 6.x kernels, but I haven't kept up with those.  You might look for performance issues with your specific kernel.  To see if that's it, try booting from the last kernel that worked fine. Usually 3 kernels are retained in the Advanced Grub Menu.  It would be good to know if all kernels or just 1 are slow.  I did see a few reports that running virtual machines under a v6.5.x kernel had huge performance issues.


Can I downgrade the kernel? Today my system completely froze.

---

### Post by MAFoElffen on 2024-02-08
Have you tried, at the Grub2 Boot Menu, using Advanced Options, booting from an earlier kernel, and had the same problems or had them resolved by that?

Have you at the Graphical Login Screen (GDM3), at the password login panel, selected the Gear Icon, to switch which Graphics Engine (Wayland or Xorg) to see if one or the other resolves your issue?

There are many things to try yet...

---

### Post by honzap00 on 2024-02-09
> **MAFoElffen said:**
> Have you tried, at the Grub2 Boot Menu, using Advanced Options, booting from an earlier kernel, and had the same problems or had them resolved by that?

Have you at the Graphical Login Screen (GDM3), at the password login panel, selected the Gear Icon, to switch which Graphics Engine (Wayland or Xorg) to see if one or the other resolves your issue?

There are many things to try yet...

Yes, when I logged in I selected Xorg. I noticed, but such things that for example Ubuntu Software starts, but the graphics do not load (when logging back into Wayland everything OK) 

I am now testing kernel version 5.19 but after logging in I don't have the correct resolution and the touchpad and keyboard don't work, using USB they do

---

### Post by honzap00 on 2024-02-09
I also noticed that it's not just a Firefox problem, as I originally thought. But the applications themselves start slowly. And the graphics on the 4K monitor are not quite sharp and nice - but that's just me. Now I'm talking about Wayland and Kernel 6.5.0.17

---

### Post by honzap00 on 2024-02-13
Do you have any tips on what to try? 
We want to deploy ubuntu in a corporate environment, can paid ubuntu support help me with the solution? Does anyone have any experience, please?

---

