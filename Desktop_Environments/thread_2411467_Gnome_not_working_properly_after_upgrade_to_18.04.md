---
title: "Gnome not working properly after upgrade to 18.04"
date: 2019-01-30
forum: Desktop Environments
---

### Post by dfpd62 on 2019-01-30
Just upgraded to 18.04 and have found a major screen issue.

The machine boots OK to a blank purple screen, but if I press enter and type my password Gnome boots my normal desktop wallpaper and screen resolution.

The problem is that nothing else works, there are no screen icons, no sidebar, no info bar at the top of the screen.

the only thing that works is right clicking on the desktop and choosing "Open Terminal" I can troubleshoot from there but the only program i've been able to run from there is Firefox (tried chromium, terminal says its running but nothing appears on screen but a Youtube video can be heard playing through the headphones).

At Reboot if I choose "Rescue" and start with "failsafe graphics" all works as it should, the screen icons, sidebar and activities bar work properly but with VGA resolution 1024x768.

This is what I've found out so far.

```

dd@dd-desktop:~$ sudo lshw -C video
 
  *-display                 
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:37 memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:c0000-dffff

```


```

dd@dd-desktop:~$ lsmod |grep radeon
radeon               1470464  20
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
drm_kms_helper        172032  1 radeon
drm                   401408  16 drm_kms_helper,radeon,ttm
dd@dd-desktop:~$ grep -r radeon /etc/modprobe.d
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist radeonfb

```

I think this shows that the correct driver is loaded and running 
Therefore I think the issue must be with Gnome.
Anyone else had anything like this?

Cheers D.

---

### Post by #&amp;thj^% on 2019-01-30
Please give this a try:
```
sudo tasksel install ubuntu-desktop

```
This will install a FULL Gnome DE.
you may first need to install "taskel" I can't remember.
```
sudo apt install tasksel
```
To start Gnome session on a system without a current graphical user interface (GUI), login to your console and execute:
```

sudo service gdm3 start

```

Otherwise, log out from your current GUI session and select GNOME session as your default desktop manager. Alternatively reboot your system if necessary.
To perform a vanilla installation of Gnome desktop execute the following:
```
sudo apt install gnome-session gdm3

``` 
Good Luck

---

### Post by dfpd62 on 2019-01-30
Even though Gnome behaves normally when booted in safe graphics (VGA) mode?

---

### Post by #&amp;thj^% on 2019-01-31
Seems support for these cards are not quite up to snuff yet: [https://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](https://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)
I could not find your card listed as supported in the above link.
i've seen problems listed on a few distros not just Ubuntu.
Well then maybe try gathering essential troubleshooting information:
```
lspci -nnk | egrep -i '3d|aphics|display|nouveau|nvidia|radeon|trident|vesa|vga'; uname -a; Xorg -version; sudo apt-get update; sudo apt-get install mesa-utils hardinfo fbset nux-tools inxi; inxi -F; sudo fbset -i; apt-cache show xserver-xorg | grep Version; xrandr; fglrxinfo; nvidia-settings -g |head -n 30 ; sudo lshw -short; sudo lshw -C display; dpkg -l | egrep -i 'fgl|intel|mesa|mesa-utils|nvidia|nouveau|radeon|trident|video-ati'; cat /etc/lsb-release; dmesg | egrep -i  'abort|ailed|bug|error|fail|fgl|GLX|GPU|intel|missing|nouveau|NVIDIA|radeon|segment|trident|VESA|VGA|wfb|\(EE\)|\(WW\)'; cat /proc/cpuinfo | grep -I model; cat /var/log/Xorg.0.log | egrep -i 'abort|ailed|bug|display|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|radeon|segment|trident|VESA|VGA|wfb|\(EE\)|\(WW\)'; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; cat /etc/X11/xorg.conf; /usr/lib/nux/unity_support_test -p; ubuntu-support-status ; sudo lsmod
```
The troubleshooters at Launchpad need to see the full Terminal output from running the above diagnostic command found here:[https://login.launchpad.net/XhQ1M2NJUp14a3XA/+decide](https://login.launchpad.net/XhQ1M2NJUp14a3XA/+decide)
EDIT: As a total stab in the dark>>>Try this for me then: Workaround:
Add "nogpumanager" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and execute update-grub to disable gpu-manger.

---

### Post by dfpd62 on 2019-01-31
Hi,
Quick note, this graphics card worked perfectly well with 16.04 and 14.04 and 12.04 .......
And it works well now, Youtube videos play as they always have.
when the mouse pointer is moved to the right edge of the screen it stops, same for the top and bottom. 
However when moved to the left side it disappears and i have move the mouse 4-5cm to get the pointer back.
Made me think that gnome has a reslution or rendering problem.

Any hoo, here is the output you wanted

```

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [1002:6779]
	Subsystem: PC Partner Limited / Sapphire Technology Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [174b:e204]
	Kernel driver in use: radeon
	Kernel modules: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM] [1002:a...
	Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 6450 1GB DDR3 [174b:aa98]
Linux dd-desktop 4.15.0-44-generic #47-Ubuntu SMP Mon Jan 14 11:26:59 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
System:    Host: dd-desktop Kernel: 4.15.0-44-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: M5A97 LE R2.0 v: Rev 1.xx serial: N/A
           UEFI: American Megatrends v: 1503 date: 01/11/2013
CPU:       6 core AMD FX-6300 Six-Core (-MCP-) cache: 12288 KB
           clock speeds: max: 3500 MHz 1: 1402 MHz 2: 1402 MHz 3: 1403 MHz
           4: 1402 MHz 5: 1424 MHz 6: 1406 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 1920x1080@60.00hz, 1680x1050@59.95hz
           OpenGL: renderer: AMD CAICOS (DRM 2.50.0 / 4.15.0-44-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-44-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: eth0 state: up speed: 100 Mbps duplex: full
           mac: 08:60:6e:59:47:71
Drives:    HDD Total Size: 1740.4GB (47.7% used)
           ID-1: /dev/sda model: WDC_WD10EVDS size: 1000.2GB
           ID-2: /dev/sdb model: Hitachi_HDS72105 size: 500.1GB
           ID-3: /dev/sdc model: SanDisk_SDSSDX24 size: 240.1GB
Partition: ID-1: / size: 212G used: 164G (82%) fs: ext4 dev: /dev/sdc2
           ID-2: swap-1 size: 8.49GB used: 0.00GB (0%)
           fs: swap dev: /dev/sdc3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 30.6C mobo: N/A gpu: 64.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 301 Uptime: 2 days Memory: 3364.7/7878.7MB
           Client: Shell (bash) inxi: 2.3.56 

mode "1680x1050"
    geometry 1680 1050 1920 1080 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : radeondrmfb
    Address     : 0xc0363000
    Size        : 8294400
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 7680
    Accelerator : No
Version: 1:7.7+19ubuntu7.1
Version: 1:7.7+19ubuntu7
Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.00*+  50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.90  
   1360x768      60.02  
   1280x800      59.91  
   1152x864      59.97  
   1280x720      59.81    60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  
   720x400       70.08  
DVI-0 connected 1680x1050+1920+0 (normal left inverted right x axis y axis) 490mm x 320mm
   1680x1050     59.95*+
   1400x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      75.04    60.00  
   1280x800      74.93  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
VGA-0 disconnected (normal left inverted right x axis y axis)
fglrxinfo: command not found

Command 'nvidia-settings' not found, but can be installed with:

sudo apt install nvidia-settings

H/W path        Device      Class       Description
===================================================
                            system      To be filled by O.E.M. (SKU)
/0                          bus         M5A97 LE R2.0
/0/0                        memory      64KiB BIOS
/0/4                        processor   AMD FX(tm)-6300 Six-Core Processor
/0/4/5                      memory      288KiB L1 cache
/0/4/6                      memory      6MiB L2 cache
/0/4/7                      memory      8MiB L3 cache
/0/2a                       memory      8GiB System Memory
/0/2a/0                     memory      4GiB DIMM DDR3 Synchronous Unbuffered (U
/0/2a/1                     memory      DIMMProject-Id-Version: lshwReport-Msgid
/0/2a/2                     memory      4GiB DIMM DDR3 Synchronous Unbuffered (U
/0/2a/3                     memory      DIMMProject-Id-Version: lshwReport-Msgid
/0/100                      bridge      RD9x0/RX980 Host Bridge
/0/100/2                    bridge      RD890/RD9x0/RX980 PCI to PCI bridge (PCI
/0/100/2/0                  display     Caicos [Radeon HD 6450/7450/8450 / R5 23
/0/100/2/0.1                multimedia  Caicos HDMI Audio [Radeon HD 6450 / 7450
/0/100/4                    bridge      RD890/RD9x0/RX980 PCI to PCI bridge (PCI
/0/100/4/0      eth0        network     RTL8111/8168/8411 PCI Express Gigabit Et
/0/100/7                    bridge      RD890/RD9x0/RX980 PCI to PCI bridge (PCI
/0/100/7/0                  bus         ASM1042 SuperSpeed USB Host Controller
/0/100/11                   storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI 
/0/100/12                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                   bus         SBx00 SMBus Controller
/0/100/14.2                 multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                 bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                 bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                 bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/16                   bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                 bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                      bridge      Family 15h Processor Function 0
/0/102                      bridge      Family 15h Processor Function 1
/0/103                      bridge      Family 15h Processor Function 2
/0/104                      bridge      Family 15h Processor Function 3
/0/105                      bridge      Family 15h Processor Function 4
/0/106                      bridge      Family 15h Processor Function 5
/0/1            scsi0       storage     
/0/1/0.0.0      /dev/sda    disk        1TB WDC WD10EVDS-63U
/0/1/0.0.0/1    /dev/sda1   volume      923GiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2   volume      8092MiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume      8092MiB Linux swap volume
/0/2            scsi2       storage     
/0/2/0.0.0      /dev/cdrom  disk        CDDVDW SH-224BB
/0/3            scsi3       storage     
/0/3/0.0.0      /dev/sdb    disk        500GB Hitachi HDS72105
/0/3/0.0.0/1    /dev/sdb1   volume      460GiB EXT4 volume
/0/3/0.0.0/2    /dev/sdb2   volume      5867MiB Extended partition
/0/3/0.0.0/2/5  /dev/sdb5   volume      5867MiB Linux swap volume
/0/5            scsi4       storage     
/0/5/0.0.0      /dev/sdc    disk        240GB SanDisk SDSSDX24
/0/5/0.0.0/1    /dev/sdc1   volume      511MiB Windows FAT volume
/0/5/0.0.0/2    /dev/sdc2   volume      215GiB EXT4 volume
/0/5/0.0.0/3    /dev/sdc3   volume      8092MiB Linux swap volume
/0/6            scsi5       storage     
/0/6/0.0.0      /dev/sdd    disk        Compact Flash
/0/6/0.0.0/0    /dev/sdd    disk        
/0/6/0.0.1      /dev/sde    disk        SM/xD-Picture
/0/6/0.0.1/0    /dev/sde    disk        
/0/6/0.0.2      /dev/sdf    disk        SD/MMC
/0/6/0.0.2/0    /dev/sdf    disk        
/0/6/0.0.3      /dev/sdg    disk        MS/MS-Pro
/0/6/0.0.3/0    /dev/sdg    disk        
  *-display                 
       description: VGA compatible controller
       product: Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:37 memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:c0000-dffff
ii  fglrx-pxpress                                         1:0.5.2.2                                    amd64        transitional package for ubuntu-drivers-common
ii  gir1.2-ibus-1.0:amd64                                 1.5.17-3ubuntu4                              amd64        Intelligent Input Bus - introspection data
ii  i965-va-driver:amd64                                  2.1.0-0ubuntu1                               amd64        VAAPI driver for Intel G45 & HD Graphics family
ii  ibus                                                  1.5.17-3ubuntu4                              amd64        Intelligent Input Bus - core
ii  ibus-gtk:amd64                                        1.5.17-3ubuntu4                              amd64        Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3:amd64                                       1.5.17-3ubuntu4                              amd64        Intelligent Input Bus - GTK+3 support
ii  intel-gpu-tools                                       1.22-1                                       amd64        tools for debugging the Intel graphics driver
ii  intel-microcode                                       3.20180807a.0ubuntu0.18.04.1                 amd64        Processor microcode firmware for Intel CPUs
ii  iucode-tool                                           2.3.1-1                                      amd64        Intel processor microcode tool
ii  libcilkrts5:amd64                                     7.3.0-27ubuntu1~18.04                        amd64        Intel Cilk Plus language extensions (runtime)
ii  libdrm-intel1:amd64                                   2.4.91-2                                     amd64        Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-intel1:i386                                    2.4.91-2                                     i386         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:amd64                                 2.4.91-2                                     amd64        Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                                  2.4.91-2                                     i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:amd64                                  2.4.91-2                                     amd64        Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                                   2.4.91-2                                     i386         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libegl-mesa0:amd64                                    18.0.5-0ubuntu0~18.04.1                      amd64        free implementation of the EGL API -- Mesa vendor library
ii  libegl1-mesa:amd64                                    18.0.5-0ubuntu0~18.04.1                      amd64        transitional dummy package
ii  libgl1-mesa-dri:amd64                                 18.0.5-0ubuntu0~18.04.1                      amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                                  18.0.5-0ubuntu0~18.04.1                      i386         free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx:amd64                                 18.0.5-0ubuntu0~18.04.1                      amd64        transitional dummy package
ii  libgl1-mesa-glx:i386                                  18.0.5-0ubuntu0~18.04.1                      i386         transitional dummy package
ii  libglapi-mesa:amd64                                   18.0.5-0ubuntu0~18.04.1                      amd64        free implementation of the GL API -- shared library
ii  libglapi-mesa:i386                                    18.0.5-0ubuntu0~18.04.1                      i386         free implementation of the GL API -- shared library
ii  libgles2-mesa:amd64                                   18.0.5-0ubuntu0~18.04.1                      amd64        transitional dummy package
ii  libglu1-mesa:amd64                                    9.0.0-2.1build1                              amd64        Mesa OpenGL utility library (GLU)
ii  libglu1-mesa:i386                                     9.0.0-2.1build1                              i386         Mesa OpenGL utility library (GLU)
ii  libglx-mesa0:amd64                                    18.0.5-0ubuntu0~18.04.1                      amd64        free implementation of the OpenGL API -- GLX vendor library
ii  libglx-mesa0:i386                                     18.0.5-0ubuntu0~18.04.1                      i386         free implementation of the OpenGL API -- GLX vendor library
ii  libibus-1.0-5:amd64                                   1.5.17-3ubuntu4                              amd64        Intelligent Input Bus - shared library
ii  libmpx0:amd64                                         5.5.0-12ubuntu1                              amd64        Intel memory protection extensions (runtime)
ii  libmpx2:amd64                                         8.2.0-1ubuntu2~18.04                         amd64        Intel memory protection extensions (runtime)
ii  libopenvg1-mesa:amd64                                 10.1.3-0ubuntu0.6                            amd64        free implementation of the OpenVG API -- runtime
rc  libtxc-dxtn-s2tc0:amd64                               0~git20131104-1.1                            amd64        Texture compression library for Mesa
rc  libtxc-dxtn-s2tc0:i386                                0~git20131104-1.1                            i386         Texture compression library for Mesa
ii  libwayland-egl1-mesa:amd64                            18.0.5-0ubuntu0~18.04.1                      amd64        implementation of the Wayland EGL platform -- runtime
ii  mesa-utils                                            8.4.0-1                                      amd64        Miscellaneous Mesa GL utilities
ii  mesa-va-drivers:amd64                                 18.0.5-0ubuntu0~18.04.1                      amd64        Mesa VA-API video acceleration drivers
ii  mesa-vdpau-drivers:amd64                              18.0.5-0ubuntu0~18.04.1                      amd64        Mesa VDPAU video acceleration drivers
ii  python-ibus                                           1.5.5-1ubuntu3.2                             all          Intelligent Input Bus - Python support
ii  xserver-xorg-video-ati                                1:18.0.1-1                                   amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-intel                              2:2.99.917+git20171229-1                     amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau                            1:1.0.15-2                                   amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon                             1:18.0.1-1                                   amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-trident                            1:1.3.8-1build1                              amd64        X.Org X server -- Trident display driver
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
[    0.000000]   Intel GenuineIntel
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20170831/tbfadt-658)
[    0.080843] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.089411] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.089415] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.129402] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[    0.129402] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.129402] pci 0000:01:00.0: vgaarb: bridge control possible
[    0.129402] vgaarb: loaded
[    1.197760] fb0: EFI VGA frame buffer device
[    1.222858] ehci-pci 0000:00:12.2: debug port 1
[    1.236529] ehci-pci 0000:00:13.2: debug port 1
[    1.252482] ehci-pci 0000:00:16.2: debug port 1
[    1.599093] Segment Routing with IPv6
[    1.599433] RAS: Correctable Errors collector initialized.
[    2.249254] [drm] radeon kernel modesetting enabled.
[    2.249319] fb: switching to radeondrmfb from EFI VGA
[    2.250117] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    2.250118] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    2.250205] [drm] radeon: 1024M of VRAM memory ready
[    2.250206] [drm] radeon: 1024M of GTT memory ready.
[    2.254609] [drm] radeon: dpm initialized
[    2.254683] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    2.255419] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    2.282408] radeon 0000:01:00.0: WB enabled
[    2.282410] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x        (ptrval)
[    2.282411] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x        (ptrval)
[    2.283180] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x        (ptrval)
[    2.283182] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    2.283214] radeon 0000:01:00.0: radeon: using MSI.
[    2.283241] [drm] radeon: irq initialized.
[    3.132954] [drm] Radeon Display Connectors
[    3.132961] [drm]   VGA-1
[    3.261833] fbcon: radeondrmfb (fb0) is primary device
[    3.261902] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    3.284911] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 0
[    3.622360] EXT4-fs (sdc2): re-mounted. Opts: errors=remount-ro
[    4.046709] snd_hda_intel 0000:01:00.1: enabling device (0000 -> 0002)
[    4.046761] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[  138.871395] Lockdown: debugfs is restricted; see man kernel_lockdown.7
[11009.464210] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[18663.815411] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[19635.071342] ata5.00: irq_stat 0x08000000, interface fatal error
[19635.071348] ata5: SError: { Handshk }
[19635.071354] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:b8:d8:74:a1/00:00:06:00:00/40 Emask 0x10 (ATA bus error)
[23612.892243] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[34951.051489] usb 2-5: device not accepting address 3, error -71
[88481.548749] ata5.00: irq_stat 0x08000000, interface fatal error
[88481.548755] ata5: SError: { Handshk }
[88481.548760] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548783] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548803] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548823] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548842] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548862] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548881] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548901] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548920] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548939] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548959] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548978] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.548997] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549017] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549036] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549055] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549075] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549095] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549114] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549133] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549153] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549172] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549191] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549210] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549230] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549249] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549272] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549291] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549311] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[88481.549330] ata5.00: failed command: WRITE FPDMA QUEUED
                        res 40/00:80:48:11:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[106347.776047] ata5.00: irq_stat 0x08000000, interface fatal error
[106347.776051] ata5: SError: { Handshk }
[106347.776054] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776067] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776079] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776090] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776101] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776112] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776123] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776134] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776145] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776155] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776166] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776177] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776188] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776199] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776210] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776221] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776231] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776242] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776253] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776264] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776275] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776285] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776296] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776307] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776318] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776329] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776340] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776350] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776361] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106347.776372] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:28:00:38:84/00:00:1a:00:00/40 Emask 0x10 (ATA bus error)
[106522.799615] ata5.00: irq_stat 0x08000000, interface fatal error
[106522.799621] ata5: SError: { Handshk }
[106522.799627] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:08:80:d2:f2/00:00:03:00:00/40 Emask 0x10 (ATA bus error)
[111287.332766] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[127040.008448] ata5.00: irq_stat 0x08000000, interface fatal error
[127040.008454] ata5: SError: { Handshk }
[127040.008461] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:d0:80:ab:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[127040.008483] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:d0:80:ab:59/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[138270.362332] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[138270.751859] Btrfs loaded, crc32c=crc32c-intel
[142376.809105] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[149751.804018] ata5.00: irq_stat 0x08000000, interface fatal error
[149751.804024] ata5: SError: { Handshk }
[149751.804030] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804052] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804072] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804091] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804110] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804129] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804148] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[149751.804167] ata5.00: failed command: WRITE FPDMA QUEUED
                         res 40/00:70:a0:22:08/00:00:07:00:00/40 Emask 0x10 (ATA bus error)
[155411.693352] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[158351.865627] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
[176764.153153] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.069] (==) Automatically adding GPU devices
[    30.069] (==) Automatically binding GPU devices
[    30.069] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.069] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    30.070] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    30.070] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    30.070] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    30.076] (II) LoadModule: "glx"
[    30.076] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.077] (II) Module glx: vendor="X.Org Foundation"
[    30.077] (==) Matched vesa as autoconfigured driver 3
[    30.141] (II) LoadModule: "radeon"
[    30.142] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.144] (II) Module radeon: vendor="X.Org Foundation"
[    30.145] (II) LoadModule: "vesa"
[    30.145] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.145] (II) Module vesa: vendor="X.Org Foundation"
[    30.145] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
	ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
	ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
	ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
	ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
	ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
	ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
	ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
	ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
	ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
	ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
	ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
	ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
	ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
	ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
	ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
	ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
	ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
	ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
	ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
	ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
	ATI Radeon 9800PRO, ATI Radeon 9800XT,
	ATI Radeon Mobility 9600/9700 (M10/M11),
	ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
	ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
	ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
	ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
	ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
	ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
	ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
	ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
	ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
	ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
	ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
	ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
	ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
	ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
	ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
	ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
	ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
	ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
	ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
	ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
	ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
	ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
	ATI FireGL V3350, ATI Mobility Radeon X1450,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
	ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
	ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
	ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
	ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
	ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
	ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
	ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
	ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
	ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
	ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
	ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
	ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
	ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
	ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
	REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
	ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
[    30.149] (II) VESA: driver for VESA chipsets: vesa
[    30.149] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[    30.150] (EE) open /dev/dri/card0: No such file or directory
[    30.150] (WW) Falling back to old probe method for modesetting
[    30.150] (EE) open /dev/dri/card0: No such file or directory
[    30.150] (WW) Falling back to old probe method for vesa
[    30.150] (EE) Screen 0 deleted because of no matching config section.
[    30.150] (II) UnloadModule: "radeon"
[    30.150] (EE) Screen 0 deleted because of no matching config section.
[    30.150] (II) FBDEV(0): Creating default Display subsection in Screen section
[    30.150] (II) FBDEV(0): hardware: EFI VGA (video memory: 3072kB)
[    30.152] (II) UnloadModule: "vesa"
[    30.152] (II) Unloading vesa
[    30.158] (II) AIGLX: Screen 0 is not DRI2 capable
[    30.158] (EE) AIGLX: reverting to software rendering
[    30.197] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[    30.198] (II) IGLX: Loaded and initialized swrast
[    30.198] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[197249.014] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[197249.014] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[197249.014] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
	Release Date: 01/11/2013
		Serial services are supported (int 14h)
	Manufacturer: To be filled by O.E.M.
	Product Name: To be filled by O.E.M.
	Serial Number: To be filled by O.E.M.
	Manufacturer: ASUSTeK COMPUTER INC.
	Product Name: M5A97 LE R2.0
	Serial Number: 121104133600323
	Manufacturer: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Manufacturer: AMD              
	Serial Number: To Be Filled By O.E.M.
	Manufacturer: Undefined    
	Serial Number: A9014E6
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Manufacturer: Undefined    
	Serial Number: A00EB42
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
cat: /etc/X11/xorg.conf: No such file or directory
OpenGL vendor string:   X.Org
OpenGL renderer string: AMD CAICOS (DRM 2.50.0 / 4.15.0-44-generic, LLVM 6.0.0)
OpenGL version string:  3.0 Mesa 18.0.5

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Support status summary of 'dd-desktop':

You have 539 packages (17.6%) supported until April 2021 (Community - 3y)
You have 1899 packages (62.0%) supported until April 2023 (Canonical - 5y)
You have 2 packages (0.1%) supported until April 2021 (Canonical - 3y)
You have 3 packages (0.1%) supported until January 2019 (Community - 9m)

You have 323 packages (10.5%) that can not/no longer be downloaded
You have 299 packages (9.8%) that are unsupported


Run with --show-unsupported, --show-supported or --show-all to see more details
Module                  Size  Used by
btrfs                1122304  0
zstd_compress         163840  1 btrfs
xor                    24576  1 btrfs
raid6_pq              114688  1 btrfs
ufs                    77824  0
qnx4                   16384  0
hfsplus               106496  0
hfs                    57344  0
minix                  32768  0
ntfs                  102400  0
msdos                  20480  0
jfs                   188416  0
xfs                  1200128  0
libcrc32c              16384  1 xfs
nls_iso8859_1          16384  1
edac_mce_amd           28672  0
kvm_amd                86016  0
kvm                   598016  1 kvm_amd
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_hda_codec_realtek   106496  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  10
aesni_intel           188416  0
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
aes_x86_64             20480  1 aesni_intel
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
snd_hwdep              20480  1 snd_hda_codec
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
serio_raw              16384  0
snd_seq_midi           16384  0
eeepc_wmi              16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
input_leds             16384  0
asus_wmi               28672  1 eeepc_wmi
snd_rawmidi            32768  1 snd_seq_midi
joydev                 24576  0
sparse_keymap          16384  1 asus_wmi
video                  45056  1 asus_wmi
wmi_bmof               16384  0
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
k10temp                16384  0
fam15h_power           16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  31 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
uas                    24576  0
usb_storage            69632  1 uas
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
radeon               1470464  24
i2c_algo_bit           16384  1 radeon
ttm                   106496  1 radeon
mxm_wmi                16384  0
drm_kms_helper        172032  1 radeon
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
drm                   401408  16 drm_kms_helper,radeon,ttm
ahci                   40960  4
i2c_piix4              24576  0
r8169                  86016  0
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    24576  3 asus_wmi,wmi_bmof,mxm_wmi

```

I will soldier on with only using Terminal for now, just have to find the proper names of the programs i wish to run :(

Ta for helping  D

---

### Post by dfpd62 on 2019-02-01
Spoke too soon,

tried to launch nautilus from the terminal and got this output.
and no window appeared.

```

dd@dd-desktop:~$ nautilus
Nautilus-Share-Message: 15:29:18.478: Called "net usershare info" but it failed: 'net usershare' returned error 255: mkdir failed on directory /var/run/samba/msg.lock: Permission denied
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Could all this be a permissions issue? did the upgrade change some?
Wouldn't be the first time.....

Ta  D.

---

### Post by #&amp;thj^% on 2019-02-01
Permissions yes!  Why, I have no clue.:(
But you misunderstood me with:
**_The troubleshooters at Launchpad need to see the full Terminal output from running the above diagnostic command _**found here:[https://login.launchpad.net/XhQ1M2NJUp14a3XA/+decide](https://login.launchpad.net/XhQ1M2NJUp14a3XA/+decide)
There someone might have an idea of what the problem was from upgrading.
I would be very curious if a fresh clean install would serve you a bit better. (As you are aware there have been some big changes from 16.04 to 18.04)
EDIT: I forgot to mention, Nautilus uses the net usershare info command to get information about non-root user defined Samba shares.
Nautilus assumes there are no such shares and displays the error message it got just in case you want it.

Creating the folder "/var/lib/samba/usershares/" should prevent the message from appearing:
```

sudo mkdir -p /var/lib/samba/usershares/
```

---

