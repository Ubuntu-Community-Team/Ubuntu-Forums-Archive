---
title: "Issues With amdgpu: ATPX Hybrid Graphics"
date: 2024-06-30
forum: Desktop Environments
---

### Post by oldlinuxnewb on 2024-06-30
Hi all,

Long time MSDos/Windows users.  Started w/ MSDos 1.0 and have been using their products since then.  I decided to switch to Linux when I was not able to upgrade my system to Win11.  Glad I was not able to.  Really no desire for AI on my system.

Sorry for the long message.  Diag messages take a lot of screen space. 

System is a SAMSUNG ELECTRONICS CO., LTD. 700C6A, w/ 32gb of ram, 1tb SSD.  Purchased in 2017.  Plenty powerful to do what I need.  Has a builtin Intel card w/ an AMD Radeon RX Pro card for GPU work.  OS Ubuntu 24.04 LTS.  [https://en.wikipedia.org/wiki/AMD_Hybrid_Graphics](https://en.wikipedia.org/wiki/AMD_Hybrid_Graphics) explains the video setup.

inxi -G
Graphics:
  Device-1: Intel HD Graphics 530 driver: N/A
  Device-2: AMD Baffin [Radeon RX 460/560D / Pro 450/455/460/555/555X/560/560X] driver: N/A
  Display: wayland server: X.Org v: 23.2.6 with: Xwayland v: 23.2.6 compositor: gnome-shell v: 46.0 driver: dri: swrast gpu: N/A resolution: 2560x1440~60Hz
  API: EGL v: 1.5 drivers: kms_swrast,swrast platforms: gbm,wayland,x11,surfaceless,device
  API: OpenGL v: 4.5 vendor: mesa v: PPA renderer: llvmpipe (LLVM 17.0.6 256 bits)

If I attempt to boot straight into Ubuntu I receive a very nice blank, black screen.  After some searching of forums, trial and error and a couple of re-installs I added nomodeset to the grub file.  Now I can load Ubuntu.  But I do not believe the graphics cards are active.  GLMark2 is showing some very low numbers.  lshw -c video seems to show the same video being used as when you choose advanced options and recovery.


  *-display UNCLAIMED       
       description: Display controller
       product: Baffin [Radeon RX 460/560D / Pro 450/455/460/555/555X/560/560X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c5
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:e0000000-e01fffff ioport:e000(size=256) memory:ef300000-ef33ffff memory:ef340000-ef35ffff

  *-display UNCLAIMED
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:ee000000-eeffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
**  *-graphics**
       product: simpledrmdrmfb
       physical id: 3
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=2560,1440

Question is:  What do I need to do to get the integrated video active?  Or are they really working and am I missing something?  

TIA

OldLinuxNewb

---

