---
title: "Stuck at splash screen, 12.04, nvidia graphics card"
date: 2014-07-17
forum: Desktop Environments
---

### Post by jaapz2 on 2014-07-17
After applying updates approximately 2 weeks ago: when i boot my PC the normal way it gets stuck at the splash screen, I see 4 dots going from white to red and back to white and that's all.
I have found a partial work-around (but printer and scanner are not working, spotify doesn't work):
boot, select the recovery mode, start network, drop to root prompt, type "lightdm" and login. At least my mail works, browser etc, so most things work. Of course not the preferred situation but something is better than nothing.

I've read through many posts, removed, purged and reinstalled the nvidia drivers, ubuntu-desktop, lightdm, xserver, updated grub etc, etc, still stuck at the same problem.

My hardware
```
[FONT=courier new][SIZE=1][I]Bus info          Device      Class       Description
=====================================================
                              system      System Product Name ()
                              bus         M2N-SLI DELUXE
                              memory      128KiB BIOS
cpu@0                         processor   AMD Phenom(tm) 9350e Quad-Core Processor
                              memory      128KiB L1 cache
                              memory      512KiB L2 cache
                              memory      8GiB System Memory
                              memory      2GiB DIMM DDR 800 MHz (1.2 ns)
                              memory      2GiB DIMM DDR 800 MHz (1.2 ns)
                              memory      2GiB DIMM DDR 800 MHz (1.2 ns)
                              memory      2GiB DIMM DDR 800 MHz (1.2 ns)
pci@0000:00:00.0              memory      RAM memory
pci@0000:00:01.0              bridge      MCP55 LPC Bridge
pci@0000:00:01.1              bus         MCP55 SMBus
pci@0000:00:02.0              bus         MCP55 USB Controller
pci@0000:00:02.1              bus         MCP55 USB Controller
pci@0000:00:04.0              storage     MCP55 IDE
pci@0000:00:05.0  scsi2       storage     MCP55 SATA Controller
scsi@2:0.0.0      /dev/sda    disk        60GB OCZ-VERTEX2
scsi@2:0.0.0,1    /dev/sda1   volume      50GiB EXT4 volume
scsi@3:0.0.0      /dev/sdb    disk        1500GB SAMSUNG HD154UI
scsi@3:0.0.0,1    /dev/sdb1   volume      3905MiB Linux swap volume
scsi@3:0.0.0,2    /dev/sdb2   volume      931GiB Extended partition
                  /dev/sdb5   volume      931GiB Linux filesystem partition
pci@0000:00:05.1  scsi4       storage     MCP55 SATA Controller
scsi@4:0.0.0      /dev/sdc    disk        1500GB SAMSUNG HD154UI
scsi@4:0.0.0,1    /dev/sdc1   volume      3905MiB Linux swap volume
pci@0000:00:05.2  scsi6       storage     MCP55 SATA Controller
scsi@6:0.0.0      /dev/cdrom  disk        DRW-20B1LT
pci@0000:00:06.0              bridge      MCP55 PCI bridge
pci@0000:01:0b.0              bus         TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lyn
pci@0000:00:06.1              multimedia  MCP55 High Definition Audio
pci@0000:00:08.0  eth0        bridge      MCP55 Ethernet
pci@0000:00:09.0  eth1        bridge      MCP55 Ethernet
pci@0000:00:0e.0              bridge      MCP55 PCI Express bridge
pci@0000:00:0f.0              bridge      MCP55 PCI Express bridge
pci@0000:03:00.0              display     G73 [GeForce 7300 GT]
pci@0000:00:18.0              bridge      Family 10h Processor HyperTransport Configuration
pci@0000:00:18.1              bridge      Family 10h Processor Address Map
pci@0000:00:18.2              bridge      Family 10h Processor DRAM Controller
pci@0000:00:18.3              bridge      Family 10h Processor Miscellaneous Control
pci@0000:00:18.4              bridge      Family 10h Processor Link Control[/I][/SIZE][/FONT]

```
The installed video-drivers
```
[SIZE=1][I][FONT=courier new]jaap@PhenomX2:~$ dpkg-query --list nvidia*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
un  nvidia-173          <none>              (no description available)
un  nvidia-173-modalias <none>              (no description available)
un  nvidia-180-modalias <none>              (no description available)
un  nvidia-185-modalias <none>              (no description available)
ii  nvidia-304          304.116-0ubuntu0.0. NVIDIA binary Xorg driver, kernel module and VDPAU lib
ii  nvidia-304-updates  304.116-0ubuntu0.0. NVIDIA binary Xorg driver, kernel module and VDPAU lib
un  nvidia-304-updates- <none>              (no description available)
ii  nvidia-319          331.20-0ubuntu0.0.2 Transitional package for nvidia-331
ii  nvidia-319-updates  331.38-0ubuntu0.0.1 Transitional package for nvidia-331-updates
ii  nvidia-319-updates- 331.38-0ubuntu0.0.1 Transitional package for nvidia-331-updates-dev
ii  nvidia-331          331.20-0ubuntu0.0.2 NVIDIA binary Xorg driver, kernel module and VDPAU lib
ii  nvidia-331-updates  331.38-0ubuntu0.0.1 NVIDIA binary Xorg driver, kernel module and VDPAU lib
ii  nvidia-331-updates- 331.38-0ubuntu0.0.1 NVIDIA binary Xorg driver development files
un  nvidia-331-updates- <none>              (no description available)
un  nvidia-331-uvm      <none>              (no description available)
un  nvidia-96-modaliase <none>              (no description available)
ii  nvidia-common       1:0.2.44.2          Find obsolete NVIDIA drivers
ii  nvidia-current      304.116-0ubuntu0.0. Transitional package for nvidia-current
un  nvidia-current-moda <none>              (no description available)
ii  nvidia-current-upda 304.116-0ubuntu0.0. Transitional package for nvidia-current-updates
un  nvidia-current-upda <none>              (no description available)
ii  nvidia-experimental 304.116-0ubuntu0.0. Transitional package for nvidia-experimental-304
ii  nvidia-experimental 319.32-0ubuntu0.0.1 Transitional package for nvidia-experimental-310
un  nvidia-libvdpau     <none>              (no description available)
un  nvidia-libvdpau-ia3 <none>              (no description available)
un  nvidia-libvdpau1    <none>              (no description available)
un  nvidia-libvdpau1-ia <none>              (no description available)
ii  nvidia-settings     331.20-0ubuntu0.0.1 Tool for configuring the NVIDIA graphics driver
un  nvidia-settings-304 <none>              (no description available)
ii  nvidia-settings-319 331.20-0ubuntu0.0.1 Transitional package for nvidia-settings
ii  nvidia-settings-319 331.20-0ubuntu0.0.1 Transitional package for nvidia-settings
ii  nvidia-settings-exp 331.20-0ubuntu0.0.1 Transitional package for nvidia-settings
un  nvidia-settings-upd <none>              (no description available)
un  nvidia-vdpau-driver <none>              (no description available)
un  nvidia-vdpau-driver <none>              (no description available)
[/FONT][/I][/SIZE]
```
My grub-file
```
[SIZE=1][I][FONT=courier new]# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
GRUB_INIT_TUNE="480 440 1"[/FONT][/I][/SIZE]
```

Does anyone have any idea how to fix this? I've used Ubuntu now for may years, had my share of little problems and worked them out but this is the first time I'm stuck on one. Any help or guidance will be highly appreciated

---

### Post by jaapz2 on 2014-07-18
Still no idea why it wasn't working. Fixed it (or worked around it) by upgrading to 14.04 LTS.
Thread can be closed.

---

