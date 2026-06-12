---
title: "XPS One 27 / 2710 compatibility"
date: 2012-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bruceliz on 2012-06-25
Has anyone installed Ubuntu on [Dell's alternative to the 27-inch iMac]("http://www.anandtech.com/show/5866/dell-xps-one-2710-review-the-premium-allinone/")?

It has some obvious advantages including easier disassembly, some upgradeability, and potentially better compatibility with Linux.

Or maybe not. Dell's vague and ambiguous published hardware specs (e.g., it's difficult to see how the base-model's i5-3450s can be accompanied by the 'default' HD 4000 graphics, since Intel says it features HD 2500) make it a bit of a pig in a poke at this point.

---

### Post by luor_d on 2012-06-29
I am no sure about ubuntu video driver for display on 2560X1440 resolution.

---

### Post by cakalapati on 2012-08-28
I recently purchased the Dell XPS One 2710 and installed Ubuntu 12.04 64-bit.  This really is a sweet machine.  Almost everything works out of the box.

What works out of the box:
* Graphics 2560X1440 resolution (defaults to Intel graphics on Core i5/i7 chip).
* Dell Wireless keyboard and mouse
* AR9485 Wireless Network Adapter 
* Sound Card can play and record sound.  Speakers are fantastic.
* Microphone
* Webcam
* Sleep and wake from Dell keyboard

Requires post-installation work:
* nVidia graphics card is tricky to get working.  I ended up going back to Intel.  No easy way to select graphics cards in Ubuntu.
* AR8161 Gigabit Ethernet  (google it on how to get it working).

lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640M] (rev a1)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
02:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.0 USB controller: Texas Instruments Device 8241 (rev 02)
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)

---

### Post by bruceliz on 2012-08-28
Many thanks, cakalapati! I've been searching for quite a while, and yours is the first reported linux install.

How happy are you with Intel HD 4000 @ 2560x1440? (I was contemplating ordering the base model without the NVidia card, except that appears to mean settling for the i5-3450S [with its less capable HD 2500 graphics]("http://www.gamersnexus.net/guides/830-ivy-bridge-specs-compared").)

---

### Post by cakalapati on 2012-08-28
That's funny.  Like you, I have been googling for a month to see if anyone bought this unit and tried to install Ubuntu on it.  The only post I found was yours.  :-)

I was struggling between the Dell XPS One 2710 and the HP Z1 (which advertises to be Linux friendly).  I only choose the Dell because my local Fry's computer store just got the Dell XPS unit in stock and I actually had a chance to play around with it.

Armed with an Ubuntu 12.04 USB key, I live booted Ubuntu in the store (with the store manager beside me of course).  Everything worked so well, I bought the machine.

The model I bought included:
Intel Core i5-3450s processor
8GB3 DDR3 SDRAM
1TB SATA 3.0Gb/s Hard Drive
NVIDIA GeForce GT 640M

I slapped in an Intel SSD and everything has been insanely  great so far.  I've had the unit for one week now.

If I were to buy the unit again, I would probably get the cheaper one (that does not include the nVidia card).  The onboard Intel graphics card is quite capable for my needs and handles the 2560x1440 resolution and GUI animations very well.

If you need me to run any commands for you, let me know.

---

### Post by cakalapati on 2012-08-28
The unit I have came with the Intel i5-3450S processor with onboard HD 2500 graphics.  While this is not a gamers graphics chip by any means, it was good for my needs (which is primarily web development).

I eventually got the nVidia card working, but the unity launcher icons on the left of the screen were really large and I could not resize them.  The config setting to resize the icons in the "Appearance" dialog, was hidden for some reason.  I'm not sure why is was hidden (disabled?) but I reverted my nVidia changes and went back to Intel.

If anyone has insight into this, I would know what happened.

---

### Post by bruceliz on 2012-08-29
> **cakalapati said:**
> The unit I have came with the Intel i5-3450S processor with onboard HD 2500 graphics.  While this is not a gamers graphics chip by any means, it was good for my needs (which is primarily web development).

Thanks for the additional info.

In a better world we'd be able to order a base unit from Dell with the i7 (HD 4000 graphics) and without the nvidia chip (and, while we're daydreaming, without Windows). Then again, in better world HP's luscious-looking Z1 would be priced 1/3 lower and thus actually _be_ luscious. ;)

---

### Post by bramvanvliet on 2012-08-31
I recently bought the Dell XPS one 2710 and installed Ubuntu 12.04 on it and it works great!! I did make some small adjustments to get the secondary GPU to work.

The model I bought included:
Intel Core i7-3770s processor
8GB3 DDR3 SDRAM
2TB SATA 3.0Gb/s Hard Drive
NVIDIA GeForce GT 640M 

lspci:
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd2 (rev a1)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
02:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
03:00.0 USB controller: Texas Instruments Device 8241 (rev 02)
04:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)

To get the secondary GPU (the NVIDIA GeForce GT 640M) to work, I installed the drivers trough the Bumblebee installation. 

```
sudo add-apt-repository ppa:bumblebee/stable
```

Then run the following:

```
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```


```
sudo gedit /etc/bumblebee/bumblebee.conf
```

and change the two followings things in the bumblebee.conf file:

1) **Replace** 
   Driver= 
   **by** 
   Driver=nvidia

2) **Replace** 
   KernelDriver=nvidia-current 
   **by** 
   KernelDriver=nvidia

Then reboot, and you should be fine for optirun.

If you want to run an application (like a game or blender) using your secondary GPU you need to run it from the command line preceded with "optirun". So if I want to run the program Blender 3D using my NVidia graphics card I would need to run:

```
optirun blender
```

---

### Post by bruceliz on 2012-08-31
Which Realtek audio chip is present, the ALC892?

```
# identify playback devices
aplay -l
```

---

### Post by bluefrog on 2012-09-01
could you issue a kvm-ok command for me please and let me know if I can have "kvm" virtualization available.

Plus, can it display TV / can you plug a TV antenna cable/wire in it?

thx
james

---

### Post by cakalapati on 2012-09-03
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


~$ sudo kvm-ok
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: Your CPU supports KVM extensions
KVM acceleration can be used

---

### Post by cakalapati on 2012-09-03
@bramvanvliet.  Thanks for the tip.  I've run into the following snag though.

(With blender installed and following your post)


~$ optirun blender
[  313.534962] [ERROR]Cannot access secondary GPU - error: You need to change the ConnectedMonitor setting in /etc/bumblebee/xorg.conf.nvidia to 

[  313.535006] [ERROR]Aborting because fallback start is disabled.


~$ cat /etc/bumblebee/xorg.conf.nvidia
Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "false"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "ConnectedMonitor" "DFP"
EndSection



~$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
#Driver=
Driver=nvidia

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
#KernelDriver=nvidia-current
KernelDriver=nvidia
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau



Any other recommendations?

---

### Post by bramvanvliet on 2012-09-07
@cakalapati I am at work right now! 
Tonight I will post my /etc/bumblebee/bumblebee.conf here so we can compare it. 

I will also post the output of the other commands.

---

### Post by XBMC old School on 2012-09-11
@cakalapati, 

Did you use a second hard drive slot or purchase a mSata SSD Drive? The online manuals aren't very good? i was hoping to do an SSD and RAM upgrades after I bought one.    

Love the thread, Been dying for an AiO for years. 2560x1600 would be sweet but i don't think i can wait that long.

---

### Post by cakalapati on 2012-09-17
I opened mine (googling the service manual will show you how to open the unit) and simply replaced the existing SATA Hard Drive with an Intel SSD hard drive.  I didn't want to mess with mSata (I needed things to just work).  The memory upgrades are relatively straight forward too.

---

### Post by afro22 on 2012-10-17
Hi, today I bought this nice piece of hardware. I didn't get chance to windows boot up first time :) 
I installed latest Ubuntu 12.10 Beta 2 abd try install bumblee. Seems to works. But seems to nvidia card is always on. There is some problem with bbswitch module.

from syslog:
```
bumblebeed[1090]: Unable to disable discrete card.
```

1) check the status 
```
root@xps:# optirun --status
Bumblebee status:  Ready (3.0.1). X inactive. Discrete video card is on.

```

2) trying disable card
```
root@xps:# tee /proc/acpi/bbswitch <<<OFF
```

3) syslog:
```
bbswitch: disabling discrete graphics
Oct 17 21:45:05 afro-xps-one-27 kernel: [ 4757.253278] bbswitch: Result of Optimus _DSM call: 00000019
Oct 17 21:45:05 afro-xps-one-27 kernel: [ 4757.253326] pci 0000:01:00.0: power state changed by ACPI to D3
```

What is your experience?

my nvidia driver: 304.43
I check GPU temperature and always around 60 degree
```
optirun nvidia-settings -c :8
```
in GPU 0 - (GeForce GT 640M) -> Thermal Settings -> Temperature

---

### Post by afro22 on 2012-10-28
Hi, 12.10 there is another bug with soundsystem. after resume from suspend state, i have no sound
see the bug [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1066488]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1066488")

any experience?

---

### Post by cakalapati on 2012-11-25
I've confirmed this bug.  No sound after resume.  If you need me to run any additional tests to help diagnose the problem, let me know.

---

### Post by sugarat on 2013-03-15
Is there a way to just permanently use the NVidia card?  I want to use it all the time so my compiz desktop is fully accelerated.

---

### Post by nossifer on 2013-11-11
Does the touchscreen function properly under linux?  Also, do you use the 32 bit or 64-AMD bit OS?  I assume the 32bit?

---

